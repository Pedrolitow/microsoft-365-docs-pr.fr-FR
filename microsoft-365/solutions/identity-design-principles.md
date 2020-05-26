---
title: 'Pour identifier et au-delà : point de vue d’un architecte'
description: Description.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: 8b991fb6cf8f03f2ff686c89251f53f53f87a5e1
ms.sourcegitcommit: 40ec697e27b6c9a78f2b679c6f5a8875dacde943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "44352545"
---
# <a name="to-identity-and-beyond--one-architects-viewpoint"></a>Pour identifier et au-delà : point de vue d’un architecte

Dans cet article, [Alex Shteynberg](https://www.linkedin.com/in/alex-shteynberg/), principal architecte technique chez Microsoft, présente les stratégies de conception principales pour les organisations d’entreprise adoptant Microsoft 365 et les autres services Cloud de Microsoft.

## <a name="about-the-author"></a>À propos de l’auteur

:::image type="content" source="../media/solutions-architecture-center/identity-and-beyond-alex-shteynberg.jpg" alt-text="Shteynberg photo d’Alex":::

Je suis un architecte technique principal dans le centre de [technologie Microsoft](https://www.microsoft.com/mtc?rtc=1)New York. Je travaille principalement avec des clients importants et des exigences complexes. Mon point de vue et ses opinions sont basés sur ces interactions et peuvent ne pas s’appliquer à toutes les situations. Toutefois, dans mon expérience, si nous pouvons aider les clients présentant les défis les plus complexes, nous pouvons aider tous les clients. 

Je travaille généralement avec plus de 100 clients chaque année. Bien que chaque organisation ait des caractéristiques uniques, il est intéressant de voir les tendances et les points communs. Par exemple, une tendance est l’intérêt de l’industrie intersectorielle pour un grand nombre de clients. Après tout, une succursale bancaire peut également être un café et un centre communautaire. 

Dans mon rôle, je me concentrerai sur la meilleure solution technique pour faire face à l’ensemble des objectifs de l’entreprise. Officiellement, je me concentre sur l’identité, la sécurité, la confidentialité et la conformité. J’adore le fait que tout ce que nous faisons. Il me donne la possibilité d’être impliqué dans la plupart des projets. Ceci me reste occupé et profite de ce rôle. 

J’habite à New York City (le meilleur !) et jouit vraiment de la diversité de sa culture, de ses denrées alimentaires et de ses personnes (pas du trafic). Je suis ravi de me déplacer quand je peux et espérons voir la plupart du monde dans mon cycle de vie. Je recherche actuellement un voyage en Afrique pour en savoir plus sur la faune sauvage.

## <a name="guiding-principles"></a>Principes de guidage 

- La **simplicité est souvent meilleure** : vous pouvez faire (presque) tout en utilisant la technologie. Cela ne signifie pas. En particulier dans l’espace de sécurité, de nombreux clients surmoteurnt les solutions. J’aime [cette vidéo](https://www.youtube.com/watch?v=SOQgABDSYZE) de la téléconférence Google pour souligner ce point.
- **Personnes, processus, technologie** — [concevoir des personnes](https://en.wikipedia.org/wiki/Human-centered_design) pour améliorer le processus, pas la technologie Tech First. Il n’existe pas de solution « parfaite ». Nous devons équilibrer les différents facteurs de risque et les décisions seront différentes pour chaque entreprise. Trop de clients conçoivent une approche que leurs utilisateurs évitent plus tard.
- **Concentrez-vous sur « pourquoi » d’abord et « comment » plus tard** , c’est le plus ennuyeux de 7 ans, avec un million de questions. Nous ne pouvons pas parvenir à la bonne réponse si nous ne connaissons pas les questions à poser. De nombreux clients font des hypothèses sur la façon dont les choses doivent travailler au lieu de définir le problème de l’entreprise. Il existe toujours plusieurs chemins d’accès.
- **Longue durée des meilleures pratiques passées** : reconnaît que les meilleures pratiques changent à la vitesse légère. Si vous avez consulté Azure AD plus de 3 mois plus tôt, vous n’êtes probablement pas à jour. Tous ces éléments sont susceptibles d’être modifiés après la publication. La « meilleure » option aujourd’hui peut ne pas être la même que dans 6 mois.

## <a name="baseline-concepts"></a>Concepts de base

N’ignorez pas cette section. Je trouve souvent que je dois revenir à ces rubriques, même pour les clients qui utilisaient des services Cloud pendant des années.
Hélas, la langue n’est pas un outil précis. Nous utilisons très souvent le même mot pour signifier différents concepts ou différents mots pour signifier le même concept. J’utilise souvent ce diagramme ci-dessous pour établir une terminologie de base et un « modèle de hiérarchie ».
<br><br>

![Illustration du client, de l’abonnement, du service et des données](../media/solutions-architecture-center/Identity-and-beyond-tenant-level.png)  

<br>

Lorsque vous apprenez à faire de même pour commencer dans le pool et pas dans le milieu de l’océan. Je n’essaie pas d’être techniquement précis avec ce diagramme. Il s’agit d’un modèle qui décrit certains concepts de base. 

Dans le schéma :
- Locataire = une instance d’Azure AD. Il se trouve au « sommet » d’une hiérarchie ou au niveau 1 du diagramme. Nous pouvons considérer qu’il s’agit de la «[limite](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-directory-independence)» où tout le reste se produit ([Azure ad B2B](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) ). Tous les services Cloud d’entreprise Microsoft font partie de l’un de ces clients. Les services grand public sont distincts. « Locataire » apparaît dans la documentation en tant que client 365 Office, client Azure, client WVD, etc. Je trouve souvent que ces variantes provoquent la confusion pour les clients.
- Services/abonnements, niveau 2 dans le diagramme, appartiennent à un seul client. La plupart des services SaaS sont 1:1 et ne peuvent pas être déplacés sans migration. Azure est différent, vous pouvez [déplacer la facturation](https://docs.microsoft.com/azure/cost-management-billing/manage/billing-subscription-transfer) et/ou un [abonnement](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) à un autre client. De nombreux clients doivent déplacer des abonnements Azure. Cela a diverses implications. Les objets qui existent en dehors de l’abonnement (par exemple, les objets RBAC et Azure AD, y compris les groupes, les applications, les stratégies, etc.) ne sont pas déplacés. Par ailleurs, certains services (coffre-fort de clés Azure, briques de données, etc.) se déplacent dans un État non fonctionnel. Ne migrez pas les services sans besoin de bonnes affaires. Certains scripts pouvant être utiles pour la migration sont [partagés sur GitHub](https://github.com/lwajswaj/azure-tenant-migration). 
- Un service donné dispose généralement d’une certaine sorte de limite de « sous-niveau », ou de niveau 3 (L3). Il est utile de comprendre la répartition de la sécurité, des stratégies, de la gouvernance, etc. Malheureusement, il n’existe pas de nom uniforme que je connais. Voici quelques exemples de noms L3 : abonnement Azure = [ressource](https://docs.microsoft.com/azure/azure-resource-manager/management/manage-resources-portal); Dynamics 365 CE = [instance](https://docs.microsoft.com/dynamics365/admin/new-instance-management); Power BI = [espace de travail](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces); Applications Power = [environnement](https://docs.microsoft.com/power-platform/admin/environments-overview); etc.
- Le niveau 4 est l’emplacement où les données réelles résident. Ce « plan de données » est une rubrique complexe. Certains services utilisent Azure AD pour RBAC, d’autres non. Je les aborderai un peu lorsque nous obtenons des rubriques de délégation.

Certains concepts supplémentaires que je trouve de nombreux clients (et employés de Microsoft) ne sont pas du tout à propos des questions suivantes :


- Tout le monde peut [créer](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant) un grand nombre de clients [sans frais](https://azure.microsoft.com/pricing/details/active-directory/). Vous n’avez pas besoin d’un service mis en service dans celui-ci. J’ai des dizaines. Chaque nom de client est unique dans le service de Cloud international de Microsoft (par exemple, deux locataires ne peuvent pas avoir le même nom). Elles sont toutes au format TenantName.onmicrosoft.com. Il existe également des processus qui créent automatiquement des clients ([clients non gérés](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-self-service-signup)). Par exemple, cela peut se produire lorsqu’un utilisateur s’inscrit à un service d’entreprise avec un domaine de messagerie qui n’existe pas dans un autre client. 
- Dans un client géré, de nombreux [domaines DNS](https://docs.microsoft.com/azure/active-directory/fundamentals/add-custom-domain) peuvent être inscrits dans celui-ci. Le nom de client d’origine n’est pas modifié. Il n’existe actuellement aucun moyen simple de renommer un client (autre que la migration). Bien que le nom du client ne soit techniquement pas critique ces jours, certains peut le trouver comme étant limitatif.
- Vous devez réserver un nom de client pour votre organisation, même si vous n’avez pas encore planifié de déploiement de services. Sinon, quelqu’un peut vous en servir et il n’existe pas de processus simple pour le reprendre (même problème que les noms DNS). J’entends cette façon trop fréquente des clients. Le nom de votre client doit également être un sujet de débat.
- Si vous possédez des espaces de noms DNS, vous devez les ajouter à vos clients. Dans le cas contraire, un [client non géré](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-self-service-signup) portant ce nom pouvait créer un locataire non géré, ce qui entraîne une interruption de [service](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover).
- L’espace de noms DNS (par exemple, contoso.com) peut appartenir à un seul client. Cela a des implications pour différents scénarios (par exemple, le partage d’un domaine de messagerie au cours d’une fusion ou d’une acquisition, etc.) Il existe un moyen d’inscrire un DNS secondaire (par exemple, div.contoso.com) dans un autre client, mais cela doit être évité. En enregistrant un nom de domaine de niveau supérieur, tous les sous-domaines sont supposés appartenir au même client. Dans les scénarios mutualisés (voir ci-dessous), je recommande normalement d’utiliser un autre nom de domaine de niveau supérieur (par exemple, contoso.ch ou ch-contoso.com).
- Qui doit « posséder » un locataire ? Je vois souvent des clients qui ne connaissent pas actuellement leur client. Il s’agit d’un grand indicateur rouge. Appelez le service d’assistance Microsoft ASAP. Tout comme le problème se pose lorsqu’un propriétaire de service (souvent un administrateur Exchange) est désigné pour gérer un client. Le client contiendra tous les services que vous pouvez utiliser à l’avenir. Le propriétaire du client doit être un groupe qui peut prendre une décision pour l’activation de tous les services Cloud au sein d’une organisation. Un autre problème est lié au fait qu’un groupe de propriétaires de clients est invité à gérer tous les services. Cette mise à l’échelle n’est pas adaptée aux grandes organisations.
- Il n’existe pas de concept de Sub/Super client. Pour une raison quelconque, ce mythe continue de se répéter. Cela s’applique également aux clients [Azure ad B2C](https://docs.microsoft.com/azure/active-directory-b2c/) . J’entends trop de fois, « mon environnement B2C fait partie de mon client XYZ » ou « comment déplacer mon client Azure vers mon client Azure 365 Office ? »
- Ce document est principalement axé sur le Cloud commercial dans le monde entier, car il s’agit de ce que la plupart des clients utilisent. Il est parfois utile de connaître les [nuages souverains](https://docs.microsoft.com/azure/active-directory/develop/authentication-national-cloud). Les nuages souverains ont des implications supplémentaires pour discuter qui sont hors de portée pour cette discussion.


## <a name="baseline-identity-topics"></a>Rubriques d’identité de base

Il existe un grand nombre de documents sur la plateforme d’identité de Microsoft : Azure Active Directory (Azure AD). Pour ceux qui commencent, il s’avère souvent écrasant. Même lorsque vous en saurez plus sur ce sujet, le maintien d’une innovation constante et d’une modification complexe peut être difficile. Dans mes interactions avec les clients, je trouve souvent « traducteur » entre les objectifs de l’entreprise et les approches « bon, meilleure, meilleure » pour les résoudre (ainsi que les « notes de falaise » de ces sujets). Il existe rarement une réponse parfaite et la décision « droite » est un équilibre entre différents facteurs de risque. Voici quelques-unes des questions courantes et des zones de confusion que j’ai tendance à discuter avec les clients.

### <a name="provisioning"></a>Mise en service
Azure AD ne résout pas le manque de gouvernance dans votre identité. La [gouvernance des identités](https://docs.microsoft.com/azure/active-directory/governance/identity-governance-overview) doit être un élément essentiel indépendamment des décisions en matière de Cloud. Les exigences de gouvernance évoluent dans le temps, c’est pourquoi il s’agit d’un programme et non d’un outil. 

Microsoft [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-azure-ad-connect) vs. [Microsoft Identity Manager](https://docs.microsoft.com/microsoft-identity-manager/microsoft-identity-manager-2016) (MIM) vs. autre chose (tierce ou personnalisée) ? Économisez de nombreux soucis à la fois et à l’avenir et accédez à Azure AD Connect. Dans cet outil, tous les types de Smarts permettent de gérer des configurations clientes et des innovations permanentes. 

Certains cas de périmètre pouvant conduire à une architecture plus complexe :
- Je dispose de plusieurs forêts Active Directory sans connectivité réseau entre celles-ci. Il existe une nouvelle option appelée [mise en service Cloud](https://docs.microsoft.com/azure/active-directory/cloud-provisioning/what-is-cloud-provisioning).
- Je n’ai pas Active Directory, ni je veux l’installer. Azure AD Connect peut être configuré pour effectuer une [synchronisation à partir de LDAP](https://docs.microsoft.com/azure/active-directory/hybrid/plan-hybrid-identity-design-considerations-tools-comparison) (le partenaire peut être requis).
- J’ai besoin de mettre en service les mêmes objets pour plusieurs clients. Cela n’est pas techniquement pris en charge, mais dépend de la définition de « même ».

Dois-je personnaliser les règles de synchronisation par défaut ([objets Filter](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering), [modifier les attributs](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized), [ID de connexion secondaire](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-userprincipalname), etc.) ? Éviter ! Une plateforme d’identité est aussi précieuse que les services qui l’utilisent. Bien que vous puissiez effectuer toutes sortes de configurations Nutty, pour répondre à cette question, vous devez examiner l’impact sur les applications. Si vous filtrez les objets à extension messagerie, la liste d’adresses globale pour les services en ligne sera incomplète ; Si l’application s’appuie sur des attributs spécifiques, le filtrage a un impact imprévisible ; etc. Il ne s’agit pas d’une décision d’équipe d’identité.

XYZ SaaS prend en charge la mise en service juste-à-temps (JIT), pourquoi est-ce que vous avez besoin de synchroniser ? Voir ci-dessus. De nombreuses applications ont besoin d’informations de profil pour les fonctionnalités. Vous ne pouvez pas avoir de lag si tous les objets à extension messagerie ne sont pas disponibles. Il en va de même pour la [mise en service des utilisateurs](https://docs.microsoft.com/azure/active-directory/app-provisioning/user-provisioning) dans les applications intégrées à Azure ad.


### <a name="authentication"></a>Authentification

[Synchronisation de hachage de mot de passe](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization) (hachage) vs. [authentification directe](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta-how-it-works) (directe) et [Fédération](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).

En règle générale, il existe un [débat](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) passionné concernant la Fédération. Il est généralement plus simple d’utiliser hachage, sauf si vous avez une bonne raison de ne pas le faire. Il est également possible de configurer différentes méthodes d’authentification pour différents domaines DNS dans le même client. 

Certains clients activent la Fédération + hachage principalement pour :
- Une option de basculement (pour la [récupération d’urgence](https://docs.microsoft.com/azure/active-directory/hybrid/plan-migrate-adfs-password-hash-sync) ) si le service de Fédération n’est pas disponible.
- Fonctionnalités supplémentaires (par exemple : [Azure AD DS](https://docs.microsoft.com/azure/active-directory-domain-services/tutorial-configure-password-hash-sync)) et services de sécurité (par exemple : [informations d’identification divulguées](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-risk-events#leaked-credentials))
- Prise en charge des services dans Azure qui ne comprennent pas l’authentification fédérée (par exemple, les [fichiers Azure](https://docs.microsoft.com/azure/storage/files/storage-files-active-directory-overview)).

J’aborde souvent les clients via le flux d’authentification client pour clarifier certaines idées. Le résultat ressemble à l’image ci-dessous, qui n’est pas aussi approprié que le processus interactif d’accès.

:::image type="content" source="../media/solutions-architecture-center/identity-beyond-whiteboard-example.png" alt-text="exemple de conversation de tableau blanc":::

Ce type de dessin de tableau blanc illustre l’endroit où les stratégies de sécurité sont appliquées dans le flux d’une demande d’authentification. Dans cet exemple, les stratégies appliquées via le service de fédération Active Directory (AD FS) sont appliquées à la première demande de service, mais pas aux demandes de service ultérieures. Il s’agit d’au moins une raison de déplacer autant que possible les contrôles de sécurité dans le Cloud.

Nous avons mis en avant le rêve de l’authentification [unique](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on) (SSO) tant que je m’en rappelle. Certains clients pensent qu’ils peuvent y parvenir en sélectionnant le fournisseur de services de Fédération « Right » (STS). Azure AD peut contribuer de manière significative à l’activation des fonctionnalités [SSO](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-sso-deployment) , mais aucun STS n’est magique. Il existe trop de méthodes d’authentification « héritées » qui sont toujours utilisées pour les applications critiques. L’extension d’Azure AD avec des [solutions partenaires](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) peut résoudre un grand nombre de ces scénarios. SSO est une stratégie et un voyage. Vous ne pouvez pas y accéder sans passer [aux normes pour les applications](https://docs.microsoft.com/azure/active-directory/develop/v2-app-types). En relation avec cette rubrique, il s’agit d’une authentification sans [mot de passe](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless) qui n’a pas non plus de réponse magique. 

[L’authentification multifacteur](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) est essentielle aujourd’hui ([ici](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984) pour plus d’informations). Ajoutez-lui une [analyse de comportement utilisateur](https://docs.microsoft.com/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) et vous disposez d’une solution qui empêche la majorité des attaques informatiques courantes. Même les services consommateurs se déplacent vers l’authentification multifacteur. Pourtant, je répond toujours à de nombreux clients qui ne souhaitent pas passer à des approches [d’authentification modernes](https://docs.microsoft.com/office365/enterprise/hybrid-modern-auth-overview) . Le plus grand argument que j’entends est qu’il aura un impact sur les utilisateurs et les applications héritées. Parfois, des clients peuvent aider les clients à se déplacer sur [les modifications annoncées](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-auth-and-exchange-online-february-2020-update/ba-p/1191282)par Exchange Online. De nombreux [rapports](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-block-legacy-authentication) Azure ad sont désormais disponibles pour aider les clients à effectuer cette transition.



### <a name="authorization"></a>Autorisation

Par [Wikipédia](https://en.wikipedia.org/wiki/Authorization), « pour autoriser » consiste à définir une stratégie d’accès. De nombreuses personnes l’considèrent comme la possibilité de définir des contrôles d’accès à un objet (fichier, service, etc.). Dans le monde actuel des menaces informatiques, ce concept évolue rapidement vers une stratégie dynamique pouvant réagir aux différents vecteurs de menace et ajuster rapidement les contrôles d’accès en réponse à ces besoins. Par exemple, si j’accède à mon compte bancaire à partir d’un emplacement inhabituel, j’obtiens des étapes de confirmation supplémentaires. Pour ce faire, nous devons prendre en considération non seulement la stratégie elle-même, mais aussi l’écosystème des méthodologies de détection de menace et de corrélation de signal.

Le moteur de stratégie d’Azure AD est implémenté à l’aide de [stratégies d’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview). Ce système repose sur des informations provenant d’un grand nombre d’autres systèmes de détection des menaces pour prendre des décisions dynamiques. Une vue simple peut ressembler à l’illustration suivante.

:::image type="content" source="../media/solutions-architecture-center/identity-and-beyond-illustration-3.png" alt-text="Moteur de stratégie dans Azure AD":::

La combinaison de tous ces signaux permet des stratégies dynamiques comme celles-ci :
- Si une menace est détectée sur votre appareil, votre accès aux données est réduit sur le Web uniquement en l’absence de possibilité de téléchargement.
- Si vous téléchargez un volume inhabituellement élevé de données, tout ce que vous téléchargez est chiffré et restreint.
- Si vous accédez à un service à partir d’un appareil non géré, vous n’êtes pas autorisé à utiliser des données hautement sensibles, mais ils sont autorisés à accéder à des données non restreintes sans avoir la possibilité de le copier dans un autre emplacement.

Si vous acceptez cette définition d’autorisation étendue, vous devez implémenter des solutions supplémentaires. Les solutions que vous implémentez dépendent de la façon dont vous souhaitez que la stratégie soit dynamique et des menaces auxquelles vous souhaitez affecter la priorité. Voici quelques exemples de systèmes de ce type :
- [Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/identity-protection/) 
- [Azure protection avancée contre les menaces](https://docs.microsoft.com/azure-advanced-threat-protection/) (Azure ATP)
- [Microsoft Defender-protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) (Microsoft Defender ATP)
- [Microsoft 365 protection avancée contre les menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide) (Microsoft 365 ATP)
- [Sécurité des applications Cloud Microsoft](https://docs.microsoft.com/cloud-app-security/) (MCAS)
- [Protection Microsoft contre les menaces](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection?view=o365-worldwide) (MTP)
- [Microsoft Intune](https://docs.microsoft.com/mem/intune/)
- [Microsoft information protection](https://docs.microsoft.com/microsoft-365/compliance/protect-information?view=o365-worldwide) (MIP)
- [Azure Sentinel](https://docs.microsoft.com/azure/sentinel/) 

Bien entendu, outre Azure AD, divers services et applications ont leurs propres modèles d’autorisation spécifiques. Certains de ces éléments sont décrits plus loin dans la section délégation.

### <a name="audit"></a>Audit
Azure AD offre [des fonctionnalités d’audit et de création de rapports](https://docs.microsoft.com/azure/active-directory/reports-monitoring/) détaillées. Toutefois, il ne s’agit généralement pas de la seule source d’informations nécessaire pour prendre des décisions en matière de sécurité. Pour plus d’informations, reportez-vous à la section délégation.

## <a name="there-is-no-exchange"></a>Il n’existe pas d’Exchange

Ne paniquez pas ! Cela ne signifie pas qu’Exchange est déconseillé (ou SharePoint, etc.). Il s’agit toujours d’un service principal. Ce que je veux dire, c’est que, pendant un certain temps, les fournisseurs de technologies ont subi des expériences utilisateur (UX) de transition pour inclure des composants de plusieurs services. Dans Microsoft 365, un exemple simple est «[pièces jointes modernes](https://support.office.com/article/Attach-files-or-insert-pictures-in-Outlook-email-messages-BDFAFEF5-792A-42B1-9A7B-84512D7DE7FC)» où les pièces jointes aux courriers électroniques sont stockées dans SharePoint Online ou OneDrive entreprise. 

:::image type="content" source="../media/solutions-architecture-center/modern-attachments.png" alt-text="joindre un fichier à un message électronique":::


En examinant le client Outlook, vous pouvez voir de nombreux services qui sont « connectés » dans le cadre de cette expérience, pas seulement Exchange. Cela inclut les groupes Azure AD, Microsoft Search, applications, Profile, conformité et Office 365. 

:::image type="content" source="../media/solutions-architecture-center/identity-and-beyond-conceptual-screenshot.png" alt-text="Interface Outlook avec légendes":::

Découvrez [Microsoft Fluid Framework](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-ignite-blog-microsoft-fluid-framework-preview/ba-p/978268) pour obtenir un aperçu des fonctionnalités à venir. En mode aperçu maintenant, je peux lire et répondre directement aux conversations de teams dans Outlook. En fait, le [client teams](https://products.office.com/microsoft-teams/download-app) est l’un des exemples les plus visibles de cette stratégie. 

Globalement, il devient de plus en plus difficile de dessiner une ligne claire entre Office 365 et d’autres services dans Microsoft Cloud. Je le visualise comme un avantage important pour les clients, car ils peuvent tirer parti de l’innovation totale pour tout ce que nous faisons, même s’ils utilisent un seul composant. C’est très sympa et cela a beaucoup de répercussions sur de nombreux clients.

Aujourd’hui, je trouve de nombreux groupes informatiques de clients sont structurés autour des « produits ». Il est logique pour un monde local, car vous avez besoin d’un expert pour chaque produit spécifique. Toutefois, je suis totalement heureux que je n’ai pas besoin de déboguer une base de données Active Directory ou Exchange dès que ces services ont été déplacés vers le Cloud. Automation (dont le type de nuage est) supprime certains travaux manuels répétitifs (Regardez ce qui s’est passé aux usines). Toutefois, celles-ci sont remplacées par des exigences plus complexes pour comprendre l’interaction entre les services, l’impact, les besoins de l’entreprise, etc. Si vous êtes disposé à [apprendre](https://docs.microsoft.com/learn/), il existe des opportunités intéressantes pour la transformation Cloud. Avant de passer en technologie, je discute souvent aux clients de la gestion des modifications apportées aux compétences informatiques et aux structures d’équipe.

Pour tous les développeurs et les responsables de déploiement SharePoint, veuillez arrêter la demande « comment puis-je créer XYZ dans SharePoint Online ? » Utilisation de [Power automate](https://docs.microsoft.com/power-automate/) (alias) pour le flux de travail, il s’agit d’une plateforme plus puissante. Utilisez [Azure bot Framework](https://docs.microsoft.com/azure/bot-service/?view=azure-bot-service-4.0) pour créer une meilleure expérience utilisateur pour votre liste d’éléments 500 Ko. Commencez à utiliser [Microsoft Graph](https://developer.microsoft.com/graph/) au lieu de CSOM. [Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview) inclut SharePoint, mais également un monde plus. Il existe de nombreux autres exemples que je peux répertorier. Il existe un grand et merveilleux univers. Ouvrez le capot et [lancez l’exploration](https://docs.microsoft.com).

L’autre impact courant se trouve dans la zone de conformité. Cette approche interservices semble entièrement confondre de nombreuses stratégies de conformité. Je continue à voir les organisations qu’il s’agit de « j’ai besoin de journaliser toutes les communications de messagerie électronique vers un système eDiscovery ». Qu’est-ce que cela signifie réellement quand le courrier électronique n’est plus simplement un courrier électronique mais une fenêtre dans d’autres services ? Office 365 a une approche complète de [la conformité](https://docs.microsoft.com/microsoft-365/compliance/), mais il est souvent plus difficile de modifier les personnes et les processus qu’avec la technologie.

Il existe de nombreuses autres implications et processus. À mon avis, il s’agit d’un domaine critique et sous-abordé. Vous avez peut-être davantage d’informations dans un autre article.

## <a name="tenant-structure-options"></a>Options de structure du client

### <a name="single-tenant-vs-multi-tenant"></a>Client unique et multi-locataire

En règle générale, la plupart des clients ne doivent avoir qu’un seul client de production. Il existe de nombreuses raisons pour lesquelles plusieurs locataires sont difficiles (leur donner une [recherche Bing](https://www.bing.com/search?q=office%20365%20multiple%20tenants)) ou lisez ce [livre blanc](https://aka.ms/multi-tenant-user). Dans le même temps, de nombreux clients d’entreprise avec lesquels je travaille ont un autre (petit) client pour l’apprentissage informatique, les tests et l’expérimentation. L’accès Azure à plusieurs clients est rendu plus facile avec [Azure phare](https://azure.microsoft.com/services/azure-lighthouse/). Office 365 et de nombreux autres services SaaS ont des limites pour les scénarios interclients. Il y a un grand nombre à prendre en compte dans les scénarios [B2B Azure ad](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) .

De nombreux clients finissent par utiliser plusieurs clients de production après une fusion et une acquisition (M&A) et veulent consolider. Aujourd’hui, cela n’est pas simple et nécessitera Microsoft Consulting Services (MCS) ou un partenaire plus un logiciel tiers. Il existe un travail d’ingénierie en cours pour répondre à divers scénarios avec des clients mutualisés à l’avenir. 

Certains clients choisissent d’utiliser plus d’un client. Il doit s’agir d’une décision très judicieuse et de la plupart des raisons commerciales. Voici quelques exemples :
- Une structure d’entreprise de type Holding où la collaboration simple entre différentes entités n’est pas requise et où les besoins d’administration et d’isolation sont forts.
- Après une acquisition, une décision d’entreprise est effectuée afin de conserver deux entités distinctes.
- Simulation de l’environnement d’un client qui ne change pas l’environnement de production du client. 
- Développement de logiciels pour les clients.

Dans ces scénarios mutualisés, les clients souhaitent souvent conserver une configuration identique pour tous les clients, ou un rapport sur les modifications de configuration et les dérives. Cela signifie souvent le passage des modifications manuelles à la configuration en tant que code. La prise en charge de Microsoft Premiere offre un atelier pour ces types d’exigences basées sur cette adresse IP publique : [https://Microsoft365dsc.com](https://Microsoft365dsc.com) .


### <a name="multi-geo"></a>Multi-Géo 

Vers [multi-géo](https://docs.microsoft.com/office365/enterprise/office-365-multi-geo) ou non à plusieurs géo, il s’agit de la question. Avec Office 365 multi-géo, vous pouvez mettre en service et stocker des données dans les emplacements géographiques où vous avez choisi de répondre aux exigences de la [résidence des données](https://docs.microsoft.com/office365/enterprise/o365-data-locations) . Il existe de nombreuses idées incertaines sur cette fonctionnalité. Gardez les éléments suivants à l’esprit : 
- Il ne fournit pas d’avantages en matière de performances. Cela peut aggraver les performances si la [conception du réseau](https://aka.ms/office365networking) est incorrecte. Obtenez des périphériques « proches » sur le réseau Microsoft, pas nécessairement pour vos données.
- Il ne s’agit pas d’une solution pour [la conformité RGPD](https://www.microsoft.com/trust-center/privacy/gdpr-overview). RGPD n’est pas centré sur la souveraineté ou les emplacements de stockage des données. Il existe d’autres structures de conformité.
- Il ne permet pas de résoudre la délégation de l’administration (voir ci-dessous) ou les [barrières d’information](https://docs.microsoft.com/microsoft-365/compliance/information-barriers).
- Il ne s’agit pas de la même chose que la fonction mutualisée et nécessite des flux de travail de [mise en service utilisateur](https:/docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) supplémentaires.
- Il ne [déplace pas votre client](https://docs.microsoft.com/office365/enterprise/moving-data-to-new-datacenter-geos) (votre Azure AD) vers une autre géographie. 

## <a name="delegation-of-administration"></a>Délégation de l’administration

Dans la plupart des grandes organisations, la séparation des tâches et le contrôle d’accès basé sur les rôles (RBAC) est une réalité nécessaire. Je suis prêt à l’avance. Ce n’est pas aussi simple que certains clients le souhaitent. Le client, le service juridique, la conformité et d’autres exigences sont différents et parfois en conflit dans le monde entier. La simplicité et la flexibilité sont souvent sur les côtés les uns des autres. Ne me faites pas mal, nous pouvons faire un meilleur travail. Des améliorations significatives ont été apportées au fil du temps. Visitez votre [Centre de technologies Microsoft](https://www.microsoft.com/mtc) local pour utiliser le modèle qui répond à vos besoins métiers sans lire 379230 documents ! Ici, je me concentrerai sur ce que vous devez réfléchir et non sur la raison d’être de cette façon. Vous trouverez ci-dessous cinq sections différentes à planifier, ainsi que certaines des questions courantes que j’ai rencontrées.

### <a name="azure-ad-and-microsoft-365-admin-centers"></a>Centres d’administration Azure AD et Microsoft 365

Il existe une liste longue et croissante de [rôles intégrés](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles). Chaque rôle se compose d’une liste d’autorisations de rôle regroupées pour permettre l’exécution d’actions spécifiques. Vous pouvez voir ces autorisations dans l’onglet « Description » à l’intérieur de chaque rôle. Vous pouvez également consulter une version plus lisible de ces éléments dans le centre d’administration 365 de Microsoft. Les définitions des rôles intégrés ne peuvent pas être modifiées. Généralement, regroupez-les en trois catégories :

- **Administrateur général** : ce rôle « tout puissant » doit être [hautement protégé](https://docs.microsoft.com/office365/enterprise/protect-your-global-administrator-accounts) comme vous le feriez dans d’autres systèmes. Les recommandations classiques sont les suivantes : aucune affectation permanente et utiliser Azure AD Privileged Identity Management (PIM); authentification forte ; etc. Il est intéressant de faire attention, ce rôle ne vous permet pas d’accéder à tous les éléments par défaut. En règle générale, je vois une confusion concernant l’accès à la conformité et l’accès à Azure, abordé plus loin. Toutefois, ce rôle peut toujours affecter l’accès à d’autres services dans le client. 
- **Administrateurs de service spécifiques** : certains services (Exchange, SharePoint, Power bi, etc.) consomment des rôles d’administration de haut niveau à partir d’Azure ad. Cette fonction n’est pas cohérente pour tous les services et il existe d’autres rôles spécifiques au service abordés plus loin.
- **Fonctionnel** : il existe une longue liste de rôles centrés sur des opérations spécifiques (invités invité, etc.). De manière périodique, de plus, d’autres sont ajoutés en fonction des besoins des clients.

Il n’est pas possible de tout déléguer (bien que l’écart soit réduit), ce qui signifie que le rôle d’administrateur global doit être utilisé parfois. La configuration en tant que code et l’automatisation doivent être considérées au lieu des personnes membres de ce rôle.

**Remarque**: le centre d’administration Microsoft 365 possède une interface plus conviviale, mais dispose de sous-ensemble de fonctionnalités par rapport à l’expérience d’administrateur Azure ad. Les deux portails utilisent les mêmes rôles Azure AD, de sorte que les modifications se produisent au même endroit. Conseil : Si vous souhaitez une interface utilisateur d’administration ciblée pour la gestion des identités sans l’encombrement Azure, utilisez [https://aad.portal.azure.com](https://aad.portal.azure.com) . 

Qu’est-ce que le nom ? N’effectuez pas d’hypothèses à partir du nom du rôle. La langue n’est pas un outil très précis. L’objectif doit être de définir les opérations qui doivent être déléguées avant de consulter les rôles nécessaires. L’ajout d’une personne au rôle « lecteur de sécurité » ne les rend pas visibles sur tous les paramètres de sécurité. 

La possibilité de créer des [rôles personnalisés](https://docs.microsoft.com/azure/active-directory/users-groups-roles/roles-custom-overview) est une question commune. Ceci est limité dans Azure AD aujourd’hui (voir ci-dessous), mais les capacités évoluent dans le temps. Je pense à ces éléments comme s’il s’agissait de fonctions dans Azure AD et peut ne pas couvrir « bas » le modèle de hiérarchie (décrit ci-dessus). Lorsque je traite « Custom », j’ai tendance à revenir à mon principal « simple ».

Une autre question fréquente est la possibilité d’étendre les rôles à un sous-ensemble d’un annuaire. Par exemple, « administrateur du support technique pour les utilisateurs de l’UE uniquement ». Les [unités administratives](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-administrative-units) (au) sont destinées à y remédier. Comme ci-dessus, je pense à celles-ci comme s’il s’agissait de fonctions dans Azure AD et peut ne pas s’étendre vers le bas. Bien entendu, certains rôles n’ont pas de sens pour l’étendue (administrateurs globaux, administrateurs de services, etc.)

À l’heure actuelle, tous ces rôles nécessitent un abonnement direct (ou une affectation dynamique si vous utilisez [Azure ad PIM](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/)). Cela signifie que les clients doivent gérer ces derniers directement dans Azure AD et ils ne peuvent pas être basés sur l’appartenance à un groupe de sécurité. Je ne suis pas fan de créer des scripts pour les gérer, car il doit être exécuté avec des droits élevés. Je recommande généralement l’intégration d’API avec des systèmes de traitement comme ServiceNow ou en utilisant des outils de gouvernance de partenaire comme Saviynt. Il y a des tâches d’ingénierie qui se font sur le long terme.

J’ai mentionné le [GIP Azure ad](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/) plusieurs fois. Il existe une solution de [gestion des accès privilégiés](https://docs.microsoft.com/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) (PAM) Microsoft Identity Manager (MIM) pour les contrôles locaux. Vous pouvez également consulter les stations de [travail à accès privilégié](https://docs.microsoft.com/windows-server/identity/securing-privileged-access/privileged-access-workstations) (pattes) et [Azure ad Identity Governance](https://docs.microsoft.com/azure/active-directory/governance/identity-governance-overview). Il existe de nombreux outils tiers qui peuvent activer l’élévation juste-à-temps, juste-suffisante et dynamique de rôles. Cela fait généralement partie d’une discussion plus importante pour la sécurisation d’un environnement. 

Parfois, les scénarios appellent l’ajout d’un utilisateur externe à un rôle (voir la section mutualisée ci-dessus). Cela fonctionne parfaitement. Le [B2B Azure ad](https://docs.microsoft.com/azure/active-directory/b2b/) est une autre rubrique intéressante et amusante pour guider les clients dans un autre article.

### <a name="security-and-compliance-center-scc"></a>Centre de sécurité et de conformité (SCC)

[Les autorisations dans le centre de sécurité & conformité Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) sont une collection de « groupes de rôles » qui sont distinctes et distinctes des rôles Azure ad. Cela peut être gênant car certains de ces groupes de rôles ont le même nom que les rôles Azure AD (par exemple, le lecteur de sécurité), mais ils peuvent avoir une appartenance différente. Je préfère l’utilisation de rôles Azure AD. Chaque groupe de rôles se compose d’un ou de plusieurs « rôles » (voir qu’est-ce que je veux faire pour réutiliser le même mot ?) et avoir des membres d’Azure AD qui sont des objets à extension messagerie. Par ailleurs, vous pouvez créer un groupe de rôles portant le même nom qu’un rôle qui peut contenir ou non ce rôle (éviter cette confusion).

En un sens, il s’agit d’une évolution du modèle de groupes de rôles Exchange. Toutefois, Exchange Online dispose de sa propre interface de [gestion de groupes de rôles](https://docs.microsoft.com/exchange/permissions-exo) . Certains groupes de rôles dans Exchange Online sont verrouillés et gérés à partir d’Azure AD ou du centre de sécurité & conformité, mais d’autres peuvent avoir des noms identiques ou similaires et sont gérés dans Exchange Online (ce qui ajoute à la confusion). Je vous recommande d’éviter d’utiliser l’interface utilisateur Exchange Online, sauf si vous avez besoin d’étendues pour la gestion d’Exchange.

Vous ne pouvez pas créer de rôles personnalisés. Les rôles sont définis par les services créés par Microsoft et s’élargiront au fur et à mesure de l’introduction de nouveaux services. Il s’agit d’un concept similaire à celui [défini par les applications](https://docs.microsoft.com/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) dans Azure ad. Lorsque de nouveaux services sont activés, les nouveaux groupes de rôles doivent souvent être créés afin d’accorder ou de déléguer l’accès à ceux-ci (par exemple, la [gestion des risques internes](https://docs.microsoft.com/microsoft-365/compliance/insider-risk-management-configure?view=o365-worldwide#step-1-required-enable-permissions-for-insider-risk-management)).

Ces groupes de rôles nécessitent également une appartenance directe et ne peuvent pas contenir de groupes Azure AD. Malheureusement, aujourd’hui ces groupes de rôles ne sont pas pris en charge par Azure AD PIM. Comme les rôles Azure AD, je tend à recommander la gestion de ces derniers via des API ou un produit de gouvernance des partenaires comme Saviynt, ou autres.

La sécurité & les rôles du centre de conformité Microsoft 365 et vous ne pouvez pas étendre ces groupes de rôles à un sous-ensemble de l’environnement (comme vous pouvez utiliser des unités administratives dans Azure AD). De nombreux clients demandent comment ils peuvent sous-déléguer. Par exemple, « créer une stratégie DLP uniquement pour les utilisateurs de l’UE ». À l’heure actuelle, si vous disposez des droits d’une fonction spécifique dans le centre de sécurité & conformité, vous disposez de droits sur tous les éléments couverts par cette fonction dans le client. Toutefois, de nombreuses stratégies ont des capacités pour cibler un sous-ensemble de l’environnement (par exemple, « rendez ces [étiquettes](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy) disponibles uniquement à ces utilisateurs »). Une bonne gouvernance et une bonne communication constituent un élément clé pour éviter les conflits. Certains clients choisissent d’implémenter une approche de « configuration en tant que code » pour résoudre la sous-délégation dans le centre de sécurité & conformité. Certains services spécifiques prennent en charge la délégation secondaire (voir ci-dessous). 

Il convient de noter que les contrôles actuellement gérés via le centre de sécurité & conformité (protection.office.com) sont en cours de migration vers deux portails d’administration distincts : security.microsoft.com et compliance.microsoft.com. Change est la seule constante !

### <a name="service-specific"></a>Spécifique au service

Comme indiqué précédemment, de nombreux clients cherchent à obtenir un modèle de délégation plus granulaire. Exemple courant : « gérer le service XYZ uniquement pour les utilisateurs et les emplacements de Division X » (ou une autre dimension). La possibilité de le faire dépend de chaque service et n’est pas cohérente entre les services et les fonctionnalités. En outre, chaque service peut avoir un modèle RBAC distinct et unique. Au lieu de discuter de tous ces éléments (il faudra toujours), j’ajoute des liens pertinents pour chaque service. Il ne s’agit pas d’une liste complète, mais elle vous permettra de démarrer.

- **Exchange Online** - [https://docs.microsoft.com/exchange/permissions-exo/permissions-exo](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo) 
- **SharePoint Online** - [https://docs.microsoft.com/sharepoint/manage-site-collection-administrators](https://docs.microsoft.com/sharepoint/manage-site-collection-administrators) 
- **Microsoft teams**  -  [https://docs.microsoft.com/microsoftteams/itadmin-readiness ](https://docs.microsoft.com/microsoftteams/itadmin-readiness )
- **Découverte** - [https://docs.microsoft.com/microsoft-365/compliance/assign-ediscovery-permissions](https://docs.microsoft.com/microsoft-365/compliance/) 
  + **Filtrage**  -  des autorisations [https://docs.microsoft.com/microsoft-365/compliance/permissions-filtering-for-content-search ](https://docs.microsoft.com/microsoft-365/compliance/)
  + **Limites**  -  de conformité [https://docs.microsoft.com/microsoft-365/compliance/set-up-compliance-boundaries ](https://docs.microsoft.com/microsoft-365/compliance/set-up-compliance-boundaries )
  + **Découverte électronique avancée**  -  [https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20 ](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20 )
- **Yammer** - [https://docs.microsoft.com/yammer/manage-yammer-users/manage-yammer-admins](https://docs.microsoft.com/yammer/manage-yammer-users/manage-yammer-admins) 
- **Multi-géo** - [https://docs.microsoft.com/office365/enterprise/add-a-sharepoint-geo-admin](https://docs.microsoft.com/office365/enterprise/add-a-sharepoint-geo-admin) 
- **Dynamics 365** –[https://docs.microsoft.com/dynamics365/](https://docs.microsoft.com/dynamics365/) <br>
  Remarque : ce lien se trouve à la racine de la documentation. Il existe plusieurs types de services avec des variantes dans le modèle d’administration/de délégation.
- **Power Platform**  -  [https://docs.microsoft.com/power-platform/admin/admin-documentation ](https://docs.microsoft.com/power-platform/admin/admin-documentation )
  + **Applications**  -  puissantes [https://docs.microsoft.com/power-platform/admin/wp-security ](https://docs.microsoft.com/power-platform/admin/wp-security ) <br>
    Remarque : il existe plusieurs types de variantes dans les modèles d’administration/de délégation.
  + Automate d’alimentation **Power Automate**  -  [https://docs.microsoft.com/power-automate/environments-overview-admin ](https://docs.microsoft.com/power-automate/environments-overview-admin )
  + **PowerBI**  -  [https://docs.microsoft.com/power-bi/service-admin-governance ](https://docs.microsoft.com/power-bi/service-admin-governance ) <br>
Remarque : la sécurité et la délégation de la plateforme de données (qui est un composant Power BI) est un domaine complexe.
- **MEM/Intune**  -  [https://docs.microsoft.com/mem/intune/fundamentals/role-based-access-control ](https://docs.microsoft.com/mem/intune/fundamentals/role-based-access-control )
- **Microsoft Defender ATP**  -  [https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles ](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles )
- **Protection contre les menaces Microsoft** - [https://docs.microsoft.com/microsoft-365/security/mtp/mtp-permissions](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-permissions)
- **Sécurité des applications Cloud Microsoft** - [https://docs.microsoft.com/cloud-app-security/manage-admins](https://docs.microsoft.com/cloud-app-security/manage-admins)
- **Stream**  -  [https://docs.microsoft.com/stream/assign-administrator-user-role ](https://docs.microsoft.com/stream/assign-administrator-user-role )
- **Barrières**  -  des informations [https://docs.microsoft.com/microsoft-365/compliance/information-barriers ](https://docs.microsoft.com/microsoft-365/compliance/information-barriers )

Pour le reste, la recherche dans docs a été réellement intéressante récemment [https://docs.microsoft.com/](https://docs.microsoft.com/microsoft-365/compliance/information-barriers) . 


### <a name="activity-logs"></a>Journaux d’activité
Office 365 dispose d’un [Journal d’audit unifié](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance). Il s’agit d’un [Journal très détaillé](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema), mais ne lit pas trop dans le nom. Il peut ne pas contenir tout ce dont vous avez besoin en matière de sécurité et de conformité. En outre, certains clients sont intéressés par l' [audit avancé](https://docs.microsoft.com/microsoft-365/compliance/advanced-audit). 

Des exemples de journaux Microsoft 365 accessibles via d’autres API sont les suivants :
- [Azure ad](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings) (activités non liées à Office 365)
- [Suivi des messages Exchange](https://docs.microsoft.com/powershell/module/exchange/get-messagetrace?view=exchange-ps)
- Systèmes de menace/UEBA présentés ci-dessus (par exemple, Azure AD Identity Protection, Microsoft Cloud App Security, Microsoft Defender ATP, etc.)
- [Protection des informations Microsoft](https://docs.microsoft.com/microsoft-365/compliance/data-classification-activity-explorer?view=o365-worldwide)
- [Microsoft Defender - PACM](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/api-power-bi)
- [Microsoft Graph](https://graph.microsoft.com)

Il est important d’identifier d’abord toutes les sources de journal requises pour un programme de sécurité et de conformité. Notez également que les différents journaux ont des limites de rétention en ligne différentes. 

Du point de vue de la délégation d’administration, la plupart des journaux d’activité de Microsoft 365 n’ont pas de modèle RBAC intégré. Si vous disposez des autorisations nécessaires pour afficher un journal, vous pouvez voir tous les éléments qu’il contient. Voici un exemple courant de l’exigence d’un client : « je veux pouvoir interroger l’activité uniquement pour les utilisateurs de l’UE » (ou une autre dimension). Pour ce faire, nous devons transférer des journaux vers un autre service. Dans le Cloud Microsoft, nous vous recommandons de le transférer vers l' [analyse de journal](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace)ou [Azure sentinelle](https://docs.microsoft.com/azure/sentinel/overview) . 

Diagramme de niveau supérieur :

![diagramme de haut niveau du flux de journal](../media/solutions-architecture-center/identity-beyond-illustration-4.png)  

Le diagramme ci-dessus représente les fonctionnalités intégrées permettant d’envoyer des journaux aux événements Hub et/ou Azure Storage et/ou Azure log Analytics. Tous les systèmes ne le sont pas encore. Toutefois, il existe d’autres approches pour envoyer ces journaux au même référentiel. Par exemple, reportez-vous à [la rubrique protection de vos équipes avec Azure Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/protecting-your-teams-with-azure-sentinel/ba-p/1265761).

La combinaison de tous les journaux dans un emplacement de stockage inclut des avantages supplémentaires, tels que des corrélations croisées, des temps de rétention personnalisés, une augmentation des données nécessaires pour prendre en charge le modèle RBAC, etc. Une fois que les données sont dans ce système de stockage, vous pouvez créer un tableau de bord PowerBI (ou un autre type de visualisation) avec un modèle RBAC approprié.

Les journaux n’ont pas à être dirigés vers un seul emplacement. Il peut également être utile d’intégrer [les journaux Office 365 avec Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) ou un modèle RBAC personnalisé dans [Power bi](https://docs.microsoft.com/microsoft-365/admin/usage-analytics/usage-analytics?view=o365-worldwide). Les différents référentiels ont des avantages et des audiences différents.

Il est important de mentionner qu’il existe un système d’analyse intégré riche en matière de sécurité, de menaces, de vulnérabilités, etc., dans un service appelé [protection contre les menaces Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection?view=o365-worldwide).

De nombreux grands clients souhaitent transférer ces données de journal vers un système tiers (par exemple, SIEM). Il existe différentes approches pour cela, mais dans-General, le [hub d’événements Azure](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs) et [Graph](https://docs.microsoft.com/graph/security-integration) sont de bonnes points de départ.


### <a name="azure"></a>Azure 
Je suis souvent invité à indiquer s’il existe un moyen de séparer les rôles à privilèges élevés entre Azure AD, Azure et SaaS (par exemple : administrateur global pour Office 365 mais pas Azure).  Pas vraiment.  L’architecture mutualisée est nécessaire si la séparation administrative complète est requise, mais cela augmente considérablement [la complexité](https://aka.ms/multi-tenant-user) (voir ci-dessus). Tous ces services font partie des mêmes limites de sécurité/identité (Regardez le modèle de hiérarchie ci-dessus).  

Il est important de comprendre les relations entre les différents services dans le même client. Je travaille avec de nombreux clients qui créent des solutions d’entreprise qui s’étendent sur Azure, Office 365 et Power Platform (et souvent également sur site et les services Cloud tiers). Voici un exemple courant : 
-   Je veux collaborer sur un ensemble de documents/images/etc (Office 365)
-   Envoyer chacun d’eux par le biais d’un processus d’approbation (Power Platform)
-   une fois que tous les composants sont approuvés, assemblez-les dans une (s) API de remise (Azure) [Microsoft Graph](https://docs.microsoft.com/azure/active-directory/develop/microsoft-graph-intro) est votre meilleur ami pour ces.  Il n’est pas possible, mais beaucoup plus complexe de concevoir une solution couvrant [plusieurs clients](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps).

Le contrôle d’accès basé sur un rôle (RBAC) Azure permet une gestion des accès affinée pour Azure. À l’aide de RBAC, vous pouvez gérer l’accès aux ressources en accordant aux utilisateurs les autorisations minimales nécessaires pour effectuer leurs tâches. Les détails sont hors de portée pour ce document, mais pour plus d’informations sur RBAC, voir [qu’est-ce que le contrôle d’accès basé sur un rôle (RBAC) dans Azure ?](https://docs.microsoft.com/azure/role-based-access-control/overview) RBAC est important, mais seulement une partie des considérations de gouvernance pour Azure. Le [cadre d’adoption](https://docs.microsoft.com/azure/cloud-adoption-framework/govern/) sur le Cloud est un excellent point de départ pour en savoir plus. J’aime comment mon ami, Andres Ravinet, parcourt pas à pas les clients par le biais de divers composants pour décider de l’approche. La vue de niveau supérieur de différents éléments (pas aussi bonne que le processus à atteindre pour le modèle de client réel) ressemble à ceci :

:::image type="content" source="../media/solutions-architecture-center/identity-beyond-illustration-5.png" alt-text="vue de niveau supérieur des composants Azure pour l’administration déléguée":::

Comme vous pouvez le voir dans l’image ci-dessus, de nombreux autres services doivent être considérés comme faisant partie de la conception (par exemple : [stratégies Azure](https://docs.microsoft.com/azure/governance/policy/overview), [plans ASURE](https://docs.microsoft.com/azure/governance/blueprints/overview), [groupes de gestion](https://docs.microsoft.com/azure/governance/management-groups/), etc.).

## <a name="conclusion"></a>Conclusion
Démarré sous forme de résumé court, terminée plus longtemps que prévu.  J’espère que vous êtes maintenant prêt à faire partie de la création d’un modèle de délégation pour votre organisation.  Cette conversation est très courante pour les clients. Il n’existe pas de modèle qui fonctionne pour tout le monde. En attendant les améliorations planifiées de l’ingénierie Microsoft avant de documenter des modèles communs, nous voyons tous les clients. En attendant, vous pouvez collaborer avec votre équipe de compte Microsoft pour organiser une visite vers le [Centre technologique Microsoft](https://www.microsoft.com/mtc)le plus proche.  Voyez-le !


