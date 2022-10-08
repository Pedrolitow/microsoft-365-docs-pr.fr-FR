---
title: 'Migrer vers Microsoft Defender pour Office 365 phase 3 : Intégration'
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
- m365-security
- m365solution-mdo-migration
- highpri
ms.custom: migrationguides
description: Effectuez les étapes de migration d’un service ou d’un appareil de protection tiers vers Microsoft Defender pour Office 365 protection.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: ce2f5011de4cce53a5ca4a03228e9563da59d996
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68079972"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-3-onboard"></a>Migrer vers Microsoft Defender pour Office 365 - Phase 3 : Intégration

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

<br>

|[![Phase 1 : Préparer.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Phase 1 : préparation](migrate-to-defender-for-office-365-prepare.md)|[![Phase 2 : Configurer.](../../media/phase-diagrams/setup.png#lightbox)](migrate-to-defender-for-office-365-setup.md) <br> [Phase 2 : configuration](migrate-to-defender-for-office-365-setup.md)|![Phase 3 : Intégration.](../../media/phase-diagrams/onboard.png) <br> Phase 3 : intégration|
|---|---|---|
|||*Vous êtes là !*|

Bienvenue dans **la phase 3 : Intégration** de votre **[migration vers Microsoft Defender pour Office 365](migrate-to-defender-for-office-365.md#the-migration-process)** ! Cette phase de migration comprend les étapes suivantes :

1. [Commencer à intégrer Security Teams](#step-1-begin-onboarding-security-teams)
2. [(Facultatif) Exempter les utilisateurs pilotes du filtrage par votre service de protection existant](#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)
3. [Paramétrer l’intelligence de l’usurpation d’identité](#step-3-tune-spoof-intelligence)
4. [Paramétrer la protection de l’emprunt d’identité et l’intelligence de boîte aux lettres](#step-4-tune-impersonation-protection-and-mailbox-intelligence)
5. [Utiliser les données des soumissions d’utilisateurs pour mesurer et ajuster](#step-5-use-data-from-user-submissions-to-measure-and-adjust)
6. [(Facultatif) Ajouter d’autres utilisateurs à votre pilote et itérer](#step-6-optional-add-more-users-to-your-pilot-and-iterate)
7. [Étendre la protection Microsoft 365 à tous les utilisateurs et désactiver la règle de flux de messagerie SCL=-1](#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)
8. [Changer vos enregistrements MX](#step-8-switch-your-mx-records)

## <a name="step-1-begin-onboarding-security-teams"></a>Étape 1 : Commencer à intégrer Security Teams

Si votre organisation dispose d’une équipe de réponse de sécurité, il est maintenant temps de commencer à intégrer Microsoft Defender pour Office 365 dans vos processus de réponse, y compris les systèmes de tickets. Il s’agit d’un sujet entier à lui-même, mais il est parfois négligé. L’implication précoce de l’équipe de réponse de sécurité garantit que votre organisation est prête à faire face aux menaces lorsque vous changez d’enregistrement MX. La réponse aux incidents doit être bien équipée pour gérer les tâches suivantes :

- Découvrez les nouveaux outils et intégrez-les aux flux existants. Par exemple :
  - Administration gestion des messages mis en quarantaine est importante. Pour obtenir des instructions, consultez [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur](manage-quarantined-messages-and-files.md).
  - La trace des messages vous permet de voir ce qui est arrivé aux messages à mesure qu’ils entrent ou quittent Microsoft 365. Pour plus d’informations, consultez la [trace des messages dans le centre d’administration Exchange moderne dans Exchange Online](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
- Identifiez les risques qui peuvent avoir été laissés dans l’organisation.
- Paramétrez et personnalisez [les alertes pour les](../../compliance/alert-policies.md) processus organisationnels.
- Gérez la file d’attente d’incidents et corrigez les risques potentiels.

Si votre organisation a acheté Microsoft Defender pour Office 365 plan 2, elle doit commencer à se familiariser avec et à utiliser des fonctionnalités telles que l’Explorateur de menaces, la chasse avancée et les incidents. Pour obtenir des formations pertinentes, consultez <https://aka.ms/mdoninja>.

Si votre équipe de réponse de sécurité collecte et analyse des messages non filtrés, vous pouvez configurer une boîte aux lettres SecOps pour recevoir ces messages non filtrés. Pour obtenir des instructions, consultez [Configurer les boîtes aux lettres SecOps dans la stratégie de remise avancée](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

### <a name="siemsoar"></a>SIEM/SOAR

Pour plus d’informations sur l’intégration à votre SIEM/SOAR, consultez les articles suivants :

- [Vue d’ensemble des API Microsoft 365 Defender](/microsoft-365/security/defender/api-overview)
- [API de diffusion en continu](/microsoft-365/security/defender/streaming-api)
- [API de recherche avancée de menaces](/microsoft-365/security/defender/api-advanced-hunting)
- [API d’incidents](/microsoft-365/security/defender/api-incident)

Si votre organisation n’a pas d’équipe de réponse de sécurité ou de flux de processus existants, vous pouvez utiliser ce temps pour vous familiariser avec les fonctionnalités de recherche et de réponse de base dans Defender pour Office 365. Pour plus d’informations, consultez [Enquête sur les menaces et réponse](office-365-ti.md).

### <a name="rbac-roles"></a>Rôles RBAC

Les autorisations dans Defender pour Office 365 sont basées sur le contrôle d’accès en fonction du rôle (RBAC) et sont expliquées dans Autorisations dans le [portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md). Voici les points importants à garder à l’esprit :

- Les rôles Azure AD accordent des autorisations à **toutes les** charges de travail dans Microsoft 365. Par exemple, si vous ajoutez un utilisateur à l’administrateur de sécurité dans le Portail Azure, il dispose d’autorisations d’administrateur de sécurité partout.
- Email & rôles de collaboration dans le portail Microsoft 365 Defender accordent des autorisations au portail Microsoft 365 Defender, au portail de conformité Microsoft Purview et à l’ancien Centre de sécurité & conformité. Par exemple, si vous ajoutez un utilisateur à l’administrateur de sécurité dans le portail Microsoft 365 Defender, il dispose **d’un** accès Administrateur de sécurité uniquement dans le portail Microsoft 365 Defender, le portail de conformité Microsoft Purview et la conformité & sécurité Centre.
- De nombreuses fonctionnalités du portail Microsoft 365 Defender sont basées sur Exchange Online applets de commande PowerShell et nécessitent donc l’appartenance à un groupe de rôles dans les rôles correspondants (techniquement, groupes de rôles) dans Exchange Online (en particulier pour l’accès au Exchange Online correspondant  Applets de commande PowerShell).
- Il existe Email & rôles de collaboration dans le portail Microsoft 365 Defender qui n’ont pas d’équivalent aux rôles Azure AD et qui sont importants pour les opérations de sécurité (par exemple, le rôle d’aperçu et le rôle De recherche et de vidage).

En règle générale, seul un sous-ensemble du personnel de sécurité a besoin de droits supplémentaires pour télécharger des messages directement à partir de boîtes aux lettres utilisateur. Cela nécessite une autorisation supplémentaire que le Lecteur de sécurité n’a pas par défaut.

## <a name="step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service"></a>Étape 2 : (Facultatif) Exempter les utilisateurs pilotes du filtrage par votre service de protection existant

Bien que cette étape ne soit pas obligatoire, vous devez envisager de configurer vos utilisateurs pilotes pour contourner le filtrage par votre service de protection existant. Cette action permet à Defender pour Office 365 de gérer **toutes les** tâches de filtrage et de protection pour les utilisateurs pilotes. Si vous n’exemptez pas vos utilisateurs pilotes de votre service de protection existant, Defender pour Office 365 fonctionne efficacement uniquement en cas d’absence de l’autre service (filtrage des messages qui ont déjà été filtrés).

> [!NOTE]
> Cette étape est explicitement requise si votre service de protection actuel fournit un habillage de liens, mais que vous souhaitez piloter la fonctionnalité Liens fiables. Le double habillage des liens n’est pas pris en charge.

## <a name="step-3-tune-spoof-intelligence"></a>Étape 3 : Paramétrer l’intelligence par usurpation d’identité

Vérifiez [l’insight sur l’usurpation](learn-about-spoof-intelligence.md) d’identité pour voir ce qui est autorisé ou bloqué en tant qu’usurpation d’identité, et pour déterminer si vous devez remplacer le verdict système pour usurpation d’identité. Certaines sources de votre e-mail critique pour l’entreprise peuvent avoir configuré de manière incorrecte les enregistrements d’authentification de messagerie dans DNS (SPF, DKIM et DMARC) et vous pouvez utiliser des remplacements dans votre service de protection existant pour masquer leurs problèmes de domaine.

L’intelligence par usurpation d’identité peut sauver les e-mails de domaines sans enregistrements d’authentification de messagerie appropriés dans DNS, mais la fonctionnalité a parfois besoin d’aide pour distinguer une bonne usurpation d’identité de l’usurpation d’identité incorrecte. Concentrez-vous sur les types de sources de messages suivants :

- Sources de messages en dehors des plages d’adresses IP définies dans [le filtrage amélioré pour les connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
- Sources de messages qui ont le plus grand nombre de messages.
- Sources de messages ayant le plus d’impact sur votre organisation.

L’intelligence par usurpation d’identité finit par se régler après avoir configuré les soumissions d’utilisateurs, il n’y a donc pas besoin de perfection.

## <a name="step-4-tune-impersonation-protection-and-mailbox-intelligence"></a>Étape 4 : Paramétrer la protection de l’emprunt d’identité et l’intelligence de boîte aux lettres

Une fois que vous avez eu suffisamment de temps pour observer les résultats de la protection contre l’emprunt d’identité dans **Ne pas appliquer de mode d’action** , vous pouvez activer individuellement chaque action de protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage :

- Protection de l’emprunt d’identité de **l’utilisateur : mettez le message en quarantaine** pour Standard et Strict.
- Protection de l’emprunt d’identité de domaine : **mettez en quarantaine le message** pour Standard et Strict.
- Protection d’intelligence de **boîte aux lettres : déplacer le message vers les dossiers Junk Email des destinataires** pour Standard ; **Mettez le message en quarantaine** pour Strict.

Plus vous surveillez les résultats de la protection de l’emprunt d’identité sans agir sur les messages, plus vous devrez identifier les autorisations ou les blocs qui peuvent être nécessaires. Envisagez d’utiliser un délai entre l’activation de chaque protection suffisamment importante pour permettre l’observation et l’ajustement.

> [!NOTE]
> La surveillance et le réglage fréquents et continus de ces protections sont importants. Si vous soupçonnez un faux positif, examinez la cause et utilisez des remplacements uniquement si nécessaire et uniquement pour la fonctionnalité de détection qui l’exige.

### <a name="tune-mailbox-intelligence"></a>Paramétrer l’intelligence de boîte aux lettres

Bien que l’intelligence de boîte aux lettres ait été configurée pour ne prendre aucune action sur les messages qui ont été [déterminés comme des tentatives d’emprunt d’identité](impersonation-insight.md), elle a été activée et a appris les modèles d’envoi et de réception de messages des utilisateurs pilotes. Si un utilisateur externe est en contact avec un de vos utilisateurs pilotes, les messages de cet utilisateur externe ne sont pas identifiés comme des tentatives d’emprunt d’identité par l’intelligence de boîte aux lettres (ce qui réduit les faux positifs).

Lorsque vous êtes prêt, effectuez les étapes suivantes pour permettre à l’intelligence de boîte aux lettres d’agir sur les messages détectés comme des tentatives d’emprunt d’identité :

- Dans la stratégie anti-hameçonnage avec les paramètres de protection Standard, modifiez la valeur de **Si l’intelligence de boîte aux lettres détecte un utilisateur usurpé d’identité** pour **déplacer le message vers les dossiers Courrier indésirable Email des destinataires**.

- Dans la stratégie anti-hameçonnage avec les paramètres de protection stricte, remplacez la valeur de **If mailbox intelligence detects and empruntersonated user** from to **Quarantine the message**.

Pour modifier les stratégies, consultez Configurer les stratégies [anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

Une fois que vous avez observé les résultats et effectué des ajustements, passez à la section suivante pour mettre en quarantaine les messages détectés par l’emprunt d’identité de l’utilisateur.

### <a name="tune-user-impersonation-protection"></a>Paramétrer la protection de l’emprunt d’identité de l’utilisateur

Dans vos deux stratégies anti-hameçonnage basées sur les paramètres Standard et Strict, modifiez la valeur de **Si le message est détecté comme un utilisateur emprunt d’identité** pour **mettre le message en quarantaine**.

Vérifiez [l’insight sur l’emprunt d’identité](impersonation-insight.md) pour voir ce qui est bloqué lors des tentatives d’emprunt d’identité de l’utilisateur.

Pour modifier les stratégies, consultez Configurer les stratégies [anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

Après avoir observé les résultats et effectué des ajustements, passez à la section suivante pour mettre en quarantaine les messages détectés par l’emprunt d’identité de domaine.

### <a name="tune-domain-impersonation-protection"></a>Paramétrer la protection de l’emprunt d’identité de domaine

Dans vos deux stratégies anti-hameçonnage basées sur les paramètres Standard et Strict, remplacez la valeur du **message If détecté comme domaine** emprunté par le **message en quarantaine**.

Vérifiez les [informations d’emprunt d’identité](impersonation-insight.md) pour voir ce qui est bloqué en tant que tentatives d’emprunt d’identité de domaine.

Pour modifier les stratégies, consultez Configurer les stratégies [anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

Observez les résultats et effectuez les ajustements nécessaires.

## <a name="step-5-use-data-from-user-submissions-to-measure-and-adjust"></a>Étape 5 : Utiliser les données des soumissions d’utilisateurs pour mesurer et ajuster

Lorsque vos utilisateurs pilotes signalent des faux positifs et des faux négatifs, les messages s’affichent sur la [page Soumissions dans le portail Microsoft 365 Defender](admin-submission.md). Vous pouvez signaler les messages mal identifiés à Microsoft à des fins d’analyse et utiliser les informations pour ajuster les paramètres et les exceptions dans vos stratégies pilotes si nécessaire.

Utilisez les fonctionnalités suivantes pour surveiller et itérer les paramètres de protection dans Defender pour Office 365 :

- [Mise en quarantaine](manage-quarantined-messages-and-files.md)
- [Threat Explorer](email-security-in-microsoft-defender.md)
- [Email rapports de sécurité](view-email-security-reports.md)
- [Rapports Defender pour Office 365](view-reports-for-mdo.md)
- [Insights sur le flux de courrier](/exchange/monitoring/mail-flow-insights/mail-flow-insights)
- [Rapports de flux de courrier](/exchange/monitoring/mail-flow-reports/mail-flow-reports)

Si votre organisation utilise un service tiers pour les rapports utilisateur, vous pouvez intégrer ces données dans votre boucle de commentaires.

## <a name="step-6-optional-add-more-users-to-your-pilot-and-iterate"></a>Étape 6 : (Facultatif) Ajouter d’autres utilisateurs à votre pilote et itérer

À mesure que vous trouvez et corrigez des problèmes, vous pouvez ajouter d’autres utilisateurs aux groupes pilotes (et, par conséquent, exempter ces nouveaux utilisateurs pilotes de l’analyse par votre service de protection existant, le cas échéant). Plus vous effectuez de tests, moins vous aurez de problèmes utilisateur à traiter ultérieurement. Cette approche « en cascade » permet de paramétrer de plus grandes parties de l’organisation et donne à vos équipes de sécurité le temps de s’adapter aux nouveaux outils et processus.

- Microsoft 365 génère des alertes lorsque les messages d’hameçonnage à haut niveau de confiance sont autorisés par les stratégies organisationnelles. Pour identifier ces messages, vous disposez des options suivantes :
  - Remplacements dans le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).
  - Filtrez dans l’Explorateur de menaces pour identifier les messages.
  - Filtrez dans La chasse avancée pour identifier les messages.

  Signalez les faux positifs à Microsoft dès que possible par le biais de soumissions d’administrateur, utilisez la fonctionnalité [Autoriser/Bloquer la liste](manage-tenant-allow-block-list.md) des locataires pour configurer des remplacements sécurisés pour ces faux positifs.

- Il est également judicieux d’examiner les remplacements inutiles. En d’autres termes, examinez les verdicts que Microsoft 365 aurait fournis sur les messages. Si Microsoft365 a rendu le verdict correct, le besoin de remplacement est considérablement réduit ou éliminé.

## <a name="step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule"></a>Étape 7 : Étendre la protection Microsoft 365 à tous les utilisateurs et désactiver la règle de flux de messagerie SCL=-1

Effectuez les étapes décrites dans cette section lorsque vous êtes prêt à basculer vos enregistrements MX vers Microsoft 365.

1. Étendez les stratégies pilotes à l’ensemble de l’organisation. Fondamentalement, il existe différentes façons de procéder :
   - Utilisez des stratégies [de sécurité prédéfinies](preset-security-policies.md) et divisez vos utilisateurs entre le profil de protection Standard et le profil de protection strict (assurez-vous que tout le monde est couvert). Les stratégies de sécurité prédéfinies sont appliquées avant toute police personnalisée que vous avez créée ou toute stratégie par défaut. Vous pouvez désactiver vos stratégies pilotes individuelles sans les supprimer.

     L’inconvénient des stratégies de sécurité prédéfinies est que vous ne pouvez pas modifier la plupart des paramètres importants une fois que vous les avez créées.

   - Modifiez l’étendue des stratégies que vous avez créées et ajustées pendant le pilote pour inclure tous les utilisateurs (par exemple, tous les destinataires dans tous les domaines). N’oubliez pas que si plusieurs stratégies du même type (par exemple, les stratégies anti-hameçonnage) s’appliquent au même utilisateur (individuellement, par appartenance au groupe ou par domaine de messagerie), seuls les paramètres de la stratégie ayant la priorité la plus élevée (numéro de priorité la plus basse) sont appliqués et le traitement s’arrête pour ce type de stratégie.

2. Désactivez la règle de flux de messagerie SCL=-1 (vous pouvez la désactiver sans la supprimer).

3. Vérifiez que les modifications précédentes ont pris effet et que Defender pour Office 365 est maintenant correctement activé pour tous les utilisateurs. À ce stade, toutes les fonctionnalités de protection de Defender pour Office 365 sont désormais autorisées à agir sur le courrier pour tous les destinataires, mais ce courrier a déjà été analysé par votre service de protection existant.

Vous pouvez effectuer une pause à ce stade pour un enregistrement et un réglage de données à plus grande échelle.

## <a name="step-8-switch-your-mx-records"></a>Étape 8 : Changer d’enregistrement MX

> [!NOTE]
>
> - Lorsque vous basculez l’enregistrement MX pour votre domaine, la propagation des modifications sur Internet peut prendre jusqu’à 48 heures.
> - Nous vous recommandons de réduire la valeur TTL de vos enregistrements DNS pour permettre une réponse plus rapide et une restauration possible (si nécessaire). Vous pouvez revenir à la valeur TTL d’origine une fois le basculement terminé et vérifié.
> - Vous devez envisager de commencer par modifier les domaines qui sont utilisés moins fréquemment. Vous pouvez suspendre et surveiller avant de passer à des domaines plus volumineux. Toutefois, même si vous effectuez cette opération, vous devez toujours vous assurer que tous les utilisateurs et tous les domaines sont couverts par des stratégies, car les domaines SMTP secondaires sont résolus en domaines principaux avant l’application de stratégie.
> - Plusieurs enregistrements MX pour un domaine unique fonctionnent techniquement, ce qui vous permet d’avoir un routage fractionné, à condition d’avoir suivi toutes les instructions de cet article. Plus précisément, vous devez vous assurer que les stratégies sont appliquées à tous les utilisateurs, que la règle de flux de messagerie SCL=-1 est appliquée uniquement aux messages qui transitent par votre service de protection existant, comme décrit à [l’étape d’installation 3 : Gérer ou créer la règle de flux de messagerie SCL=-1](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Toutefois, cette configuration introduit un comportement qui rend la résolution des problèmes beaucoup plus difficile. Par conséquent, nous ne le recommandons généralement pas, en particulier pendant des périodes prolongées.
> - Avant de basculer vos enregistrements MX, vérifiez que les paramètres suivants ne sont pas activés sur le connecteur entrant du service de protection vers Microsoft 365. En règle générale, un ou plusieurs des paramètres suivants sont configurés pour le connecteur :
>   - **et exiger que le nom d’objet sur le certificat que le partenaire utilise pour s’authentifier avec Office 365 corresponde à ce nom de domaine** (*RestrictDomainsToCertificate*)
>   - **Rejeter les messages électroniques s’ils ne sont pas envoyés à partir de cette plage d’adresses IP** (*RestrictDomainsToIPAddresses*) Si le type de connecteur est **Partner** et que l’un de ces paramètres est activé, toutes les remises de courrier à vos domaines échouent après le basculement de vos enregistrements MX. Vous devez désactiver ces paramètres avant de continuer. Si le connecteur est un connecteur local utilisé pour l’hybride, vous n’avez pas besoin de modifier le connecteur local. Toutefois, vous pouvez toujours vérifier la présence d’un connecteur **partenaire** .
> - Si votre passerelle de messagerie actuelle fournit également la validation des destinataires, vous pouvez vérifier que le domaine est configuré comme faisant [autorité](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) dans Microsoft 365. Cela peut empêcher les messages de rebond inutiles.

Lorsque vous êtes prêt, basculez l’enregistrement MX pour vos domaines. Vous pouvez migrer tous vos domaines à la fois. Vous pouvez également migrer d’abord des domaines moins fréquemment utilisés, puis migrer le reste ultérieurement.

N’hésitez pas à vous suspendre et à évaluer ici à tout moment. Mais n’oubliez pas : une fois que vous avez désactivé la règle de flux de messagerie SCL=-1, les utilisateurs peuvent avoir deux expériences différentes pour vérifier les faux positifs. Plus tôt vous pourrez fournir une expérience unique et cohérente, plus vos utilisateurs et vos équipes de support technique seront heureux lorsqu’ils devront résoudre un message manquant.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé votre [migration vers Microsoft Defender pour Office 365](migrate-to-defender-for-office-365.md#the-migration-process)! Étant donné que vous avez suivi les étapes décrites dans ce guide de migration, les premiers jours où le courrier est remis directement dans Microsoft 365 doivent être beaucoup plus fluides.

Vous commencez maintenant l’opération normale et la maintenance de Defender pour Office 365. Surveillez et surveillez les problèmes qui sont similaires à ceux que vous avez rencontrés pendant le pilote, mais à plus grande échelle. [L’insight sur l’usurpation d’identité](learn-about-spoof-intelligence.md) et l’insight d’emprunt d’identité seront les plus utiles, mais envisagez de faire des activités suivantes une occurrence régulière :[](impersonation-insight.md)

- Examiner les soumissions d’utilisateurs, en particulier les [messages d’hameçonnage signalés par l’utilisateur](automated-investigation-response-office.md)
- Passez en revue les remplacements dans le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).
- Utilisez des requêtes [De chasse avancée](/microsoft-365/security/defender/advanced-hunting-example) pour rechercher des opportunités de paramétrage et des messages à risque.
