---
title: Microsoft 365 planification des ressources d’entreprise - Architecture de sécurité
description: Découvrez les principales stratégies de conception pour l’architecture Microsoft Enterprise d’Alex Shteynberg, architecte principal technique chez Microsoft.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: b5b2f8efe36ceba10dd1dadd3034b899ad05fd38
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945448"
---
# <a name="to-identity-and-beyondone-architects-viewpoint"></a>À l’identité et au-delà : point de vue d’un architecte

Dans cet article, [Alex Shteynberg](https://www.linkedin.com/in/alex-shteynberg/), architecte technique principal chez Microsoft, décrit les principales stratégies de conception pour les organisations d’entreprise qui adoptent Microsoft 365 et d’autres services cloud Microsoft.

## <a name="about-the-author"></a>À propos de l’auteur

![Photo d’Alex Shteynberg.](../media/solutions-architecture-center/identity-and-beyond-alex-shteynberg.jpg)

Je suis architecte technique principal au [Microsoft Technology Center](https://www.microsoft.com/mtc?rtc=1) de New York. Je travaille principalement avec de gros clients et des exigences complexes. Mon point de vue et mes opinions sont fondés sur ces interactions et peuvent ne pas s’appliquer à toutes les situations. Toutefois, d’après mon expérience, si nous pouvons aider les clients avec les défis les plus complexes, nous pouvons aider tous les clients.

Je travaille généralement avec plus de 100 clients chaque année. Bien que chaque organisation ait des caractéristiques uniques, il est intéressant de voir les tendances et les points communs. Par exemple, une tendance est l’intérêt inter-secteurs pour de nombreux clients. Après tout, une succursale bancaire peut également être un café et un centre communautaire.

Dans mon rôle, je m’attache à aider les clients à trouver la meilleure solution technique pour répondre à leur ensemble unique d’objectifs métier. Officiellement, je me concentre sur l’identité, la sécurité, la confidentialité et la conformité. J’aime le fait que ces touche tout ce que nous faisons. Cela me donne l’occasion de m’impliquer dans la plupart des projets. Cela me tient très occupé et profiter de ce rôle.

Je vis à New York (le meilleur!) et j’apprécie vraiment la diversité de sa culture, de sa nourriture et de ses gens (pas de trafic). J’aime voyager quand je peux et j’espère voir la plupart du monde dans ma vie. Je recherche actuellement un voyage en Afrique pour en savoir plus sur la faune.

## <a name="guiding-principles"></a>Principes directeurs

- **La simplicité est souvent meilleure** : vous pouvez faire (presque) n’importe quoi avec la technologie, mais cela ne signifie pas que vous devriez. En particulier dans l’espace de sécurité, de nombreux clients surenginent des solutions. J’aime [cette vidéo](https://www.youtube.com/watch?v=SOQgABDSYZE) de la conférence Stripe de Google pour souligner ce point.
- **Personnes, processus, technologie**: [Conception pour les gens](https://en.wikipedia.org/wiki/Human-centered_design) d’améliorer le processus, pas la technologie d’abord. Il n’existe pas de solutions « parfaites ». Nous devons équilibrer différents facteurs de risque et les décisions seront différentes pour chaque entreprise. Trop de clients conçoivent une approche que leurs utilisateurs évitent par la suite.
- **Concentrez-vous sur « pourquoi » d’abord et « comment » plus tard**: Être le gamin ennuyeux 7 ans avec un million de questions. Nous ne pouvons pas trouver la bonne réponse si nous ne connaissons pas les bonnes questions à poser. Beaucoup de clients font des hypothèses sur la façon dont les choses doivent fonctionner au lieu de définir le problème métier. Il existe toujours plusieurs chemins d’accès qui peuvent être empruntés.
- **Longue fin des meilleures pratiques passées** : reconnaître que les meilleures pratiques changent à la vitesse de la lumière. Si vous avez examiné Azure AD il y a plus de trois mois, vous êtes probablement obsolète. Tout est susceptible d’être modifié après la publication. L’option « Best » d’aujourd’hui ne sera peut-être pas la même dans six mois.

## <a name="baseline-concepts"></a>Concepts de référence

N’ignorez pas cette section. Je trouve souvent que je dois revenir en arrière sur ces sujets, même pour les clients qui utilisent des services cloud depuis des années.
Hélas, la langue n’est pas un outil précis. Nous utilisons souvent le même mot pour désigner des concepts différents ou des mots différents pour signifier le même concept. J’utilise souvent ce diagramme ci-dessous pour établir une terminologie de base et un « modèle hiérarchique ».
<br><br>

![Illustration du locataire, de l’abonnement, du service et des données.](../media/solutions-architecture-center/Identity-and-beyond-tenant-level.png)

<br>

Quand vous apprenez à nager, il est préférable de commencer dans la piscine et non au milieu de l’océan. Je n’essaie pas d’être techniquement précis avec ce diagramme. Il s’agit d’un modèle pour discuter de certains concepts de base.

Dans le schéma :

- Locataire = instance de Azure AD. Il se trouve en « haut » d’une hiérarchie, ou au niveau 1 dans le diagramme. Nous pouvons considérer qu’il s’agit de la « [limite](/azure/active-directory/users-groups-roles/licensing-directory-independence) » où tout le reste se produit ([Azure AD B2B de](/azure/active-directory/b2b/what-is-b2b) côté). Tous les services cloud d’entreprise Microsoft font partie de l’un de ces locataires. Les services aux consommateurs sont distincts. « Locataire » apparaît dans la documentation en tant que locataire Office 365, locataire Azure, locataire WVD, et ainsi de suite. Je trouve souvent que ces variations provoquent de la confusion pour les clients.
- Les services/abonnements, niveau 2 dans le diagramme, appartiennent à un seul locataire. La plupart des services SaaS sont 1:1 et ne peuvent pas se déplacer sans migration. Azure est différent, vous pouvez [déplacer la facturation](/azure/cost-management-billing/manage/billing-subscription-transfer) et/ou un [abonnement](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) vers un autre locataire. De nombreux clients doivent déplacer des abonnements Azure. Cela a différentes implications. Les objets qui existent en dehors de l’abonnement ne se déplacent pas (par exemple, contrôle d’accès en fonction du rôle ou RBAC Azure, et Azure AD objets, notamment les groupes, les applications, les stratégies, etc.). En outre, certains services (tels qu’Azure Key Vault, Data Bricks, etc.). Ne migrez pas de services sans avoir besoin d’une bonne entreprise. Certains scripts qui peuvent être utiles pour la migration sont [partagés sur GitHub](https://github.com/lwajswaj/azure-tenant-migration).
- Un service donné a généralement une sorte de limite de « sous-niveau » ou de niveau 3 (L3). Cela est utile pour comprendre la séparation de la sécurité, des politiques, de la gouvernance, et ainsi de suite. Malheureusement, je ne connais pas de nom uniforme. Voici quelques exemples de noms pour L3 : Abonnement Azure = [ressource](/azure/azure-resource-manager/management/manage-resources-portal) ; Dynamics 365 CE = [instance](/dynamics365/admin/new-instance-management) ; Power BI = [espace de travail](/power-bi/service-create-the-new-workspaces) ; Power Apps = [environnement](/power-platform/admin/environments-overview); et ainsi de suite.
- Le niveau 4 est l’endroit où résident les données réelles. Ce « plan de données » est un sujet complexe. Certains services utilisent Azure AD pour RBAC, d’autres non. J’en discuterai un peu quand nous aborderons les sujets de délégation.

Voici quelques concepts supplémentaires que je trouve que de nombreux clients (et employés de Microsoft) sont confus ou ont des questions sur les éléments suivants :

- N’importe qui peut [créer](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant) de nombreux locataires [gratuitement](https://azure.microsoft.com/pricing/details/active-directory/). Vous n’avez pas besoin d’un service approvisionné dans celui-ci. J’en ai des dizaines. Chaque nom de locataire est unique dans le service cloud mondial de Microsoft (en d’autres termes, aucun locataire ne peut avoir le même nom). Elles sont toutes au format TenantName.onmicrosoft.com. Il existe également des processus qui créent automatiquement des locataires ([locataires non gérés](/azure/active-directory/users-groups-roles/directory-self-service-signup)). Par exemple, cela peut se produire lorsqu’un utilisateur s’inscrit à un service d’entreprise avec un domaine de messagerie qui n’existe dans aucun autre locataire.
- Dans un locataire managé, de nombreux [domaines DNS](/azure/active-directory/fundamentals/add-custom-domain) peuvent être inscrits dans celui-ci. Cela ne modifie pas le nom du locataire d’origine. Il n’existe actuellement aucun moyen simple de renommer un locataire (autre que la migration). Bien que le nom du locataire ne soit techniquement pas critique de nos jours, certains peuvent trouver cela limité.
- Vous devez réserver un nom de locataire pour votre organisation même si vous ne prévoyez pas encore de déployer des services. Sinon, quelqu’un peut vous le prendre et il n’y a pas de processus simple pour le reprendre (même problème que les noms DNS). J’entends cela trop souvent de la part des clients. Le nom de votre locataire doit également faire l’objet d’un débat.
- Si vous possédez des espaces de noms DNS, vous devez les ajouter à vos locataires. Dans le cas contraire, vous pouvez créer un [locataire non managé](/azure/active-directory/users-groups-roles/directory-self-service-signup) avec ce nom, ce qui entraîne une interruption pour [le rendre géré](/azure/active-directory/users-groups-roles/domains-admin-takeover).
- L’espace de noms DNS (tel que contoso.com) peut appartenir à un seul locataire. Cela a des implications pour différents scénarios (par exemple, le partage d’un domaine de messagerie lors d’une fusion ou d’une acquisition, etc.). Il existe un moyen d’inscrire un sous-service DNS (tel que div.contoso.com) dans un autre locataire, mais cela doit être évité. En inscrivant un nom de domaine de niveau supérieur, tous les sous-domaines sont supposés appartenir au même locataire. Dans les scénarios multilocataires (voir ci-dessous), je recommande normalement d’utiliser un autre nom de domaine de niveau supérieur (par exemple, contoso.ch ou ch-contoso.com).
- Qui devez « posséder » un locataire ? Je vois souvent des clients qui ne savent pas qui possède actuellement leur locataire. C’est un grand drapeau rouge. Appelez le support Microsoft ASAP. Tout aussi problématique est lorsqu’un propriétaire de service (souvent un administrateur Exchange) est désigné pour gérer un locataire. Le locataire contiendra tous les services que vous souhaiterez peut-être à l’avenir. Le propriétaire du locataire doit être un groupe qui peut prendre la décision d’activer tous les services cloud d’une organisation. Un autre problème se pose lorsqu’un groupe de propriétaires de locataires est invité à gérer tous les services. Cette opération n’est pas mise à l’échelle pour les grandes organisations.
- Il n’existe aucun concept de sous-locataire/super locataire. Pour une raison quelconque, ce mythe ne cesse de se répéter. Cela s’applique également aux locataires [Azure AD B2C](/azure/active-directory-b2c/). J’entends trop souvent « Mon environnement B2C se trouve dans mon locataire XYZ » ou « Comment faire déplacer mon locataire Azure dans mon locataire Office 365 ? »
- Ce document se concentre principalement sur le cloud commercial dans le monde entier, car c’est ce que la plupart des clients utilisent. Il est parfois utile de connaître les [clouds souverains](/azure/active-directory/develop/authentication-national-cloud). Les clouds souverains ont des implications supplémentaires à discuter qui sont hors de portée pour cette discussion.

## <a name="baseline-identity-topics"></a>Rubriques sur l’identité de référence

Il existe une grande documentation sur la plateforme d’identités de Microsoft : Azure Active Directory (Azure AD). Pour ceux qui ne font que commencer, il se sent souvent écrasante. Même une fois que vous l’avez appris, il peut être difficile de suivre l’innovation et le changement constants. Dans mes interactions avec les clients, je me retrouve souvent à servir de « traducteur » entre les objectifs commerciaux et les approches « Bonnes, Meilleures, Meilleures » pour répondre à ces questions (et des « notes de falaise » humaines pour ces sujets). Il y a rarement une réponse parfaite et la « bonne » décision est un équilibre entre différents facteurs de risque. Voici quelques-unes des questions courantes et les zones de confusion que j’ai tendance à discuter avec les clients.

### <a name="provisioning"></a>Approvisionnement

Azure AD ne résout pas le manque de gouvernance dans votre monde des identités ! [La gouvernance des identités](/azure/active-directory/governance/identity-governance-overview) doit être un élément critique indépendant de toute décision cloud. Les exigences de gouvernance changent au fil du temps, c’est pourquoi il s’agit d’un programme et non d’un outil.

[Azure AD Connecter](/azure/active-directory/hybrid/whatis-azure-ad-connect) ou [Microsoft Identity Manager](/microsoft-identity-manager/microsoft-identity-manager-2016) (MIM) ou autre chose (tiers ou personnalisé) ? Économisez-vous beaucoup de maux de tête maintenant et à l’avenir et aller avec Azure AD Connecter. Cet outil présente toutes sortes d’intelligence pour répondre aux configurations particulières des clients et aux innovations en cours.

Voici quelques cas de périphérie qui peuvent conduire à une architecture plus complexe :

- J’ai plusieurs forêts AD sans connectivité réseau entre ces forêts. Il existe une nouvelle option appelée [Cloud Provisioning](/azure/active-directory/cloud-provisioning/what-is-cloud-provisioning).
- Je n’ai pas Active Directory et je ne veux pas l’installer. Azure AD Connecter peut être configurée pour [la synchronisation à partir de LDAP](/azure/active-directory/hybrid/plan-hybrid-identity-design-considerations-tools-comparison) (le partenaire peut être requis).
- Je dois provisionner les mêmes objets pour plusieurs locataires. Cela n’est pas techniquement pris en charge, mais dépend de la définition de « même ».

Dois-je personnaliser les règles de synchronisation par défaut ([filtrer des objets](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering), [modifier des attributs](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized), [un autre ID de connexion](/azure/active-directory/hybrid/plan-connect-userprincipalname), et ainsi de suite) ? Évitez-le ! Une plateforme d’identité n’est aussi précieuse que les services qui l’utilisent. Bien que vous puissiez effectuer toutes sortes de configurations nutty, pour répondre à cette question, vous devez examiner l’impact sur les applications. Si vous filtrez des objets compatibles avec la messagerie, la gal pour services en ligne sera incomplète ; si l’application s’appuie sur des attributs spécifiques, leur filtrage aura un impact imprévisible, etc. Ce n’est pas une décision d’équipe d’identité.

XYZ SaaS prend en charge le provisionnement juste-à-temps (JIT), pourquoi me demandez-vous de synchroniser ? Voir ci-dessus. De nombreuses applications ont besoin d’informations de « profil » pour les fonctionnalités. Vous ne pouvez pas disposer d’une gal si tous les objets à extension messagerie ne sont pas disponibles. Il en va de même pour [le provisionnement d’utilisateurs dans les](/azure/active-directory/app-provisioning/user-provisioning) applications intégrées à Azure AD.

### <a name="authentication"></a>Authentification

[Synchronisation de hachage de mot de passe](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization) (PHS) et [authentification directe](/azure/active-directory/hybrid/how-to-connect-pta-how-it-works) (PTA) et [fédération](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).

Il y a généralement un [débat](/azure/active-directory/hybrid/choose-ad-authn) passionné autour de la fédération. Plus simple est généralement mieux et donc utiliser PHS, sauf si vous avez une bonne raison de ne pas le faire. Il est également possible de configurer différentes méthodes d’authentification pour différents domaines DNS dans le même locataire.

Certains clients activent la fédération + PHS principalement pour :

- Option permettant de [revenir](/azure/active-directory/hybrid/plan-migrate-adfs-password-hash-sync) à (pour la récupération d’urgence) si le service de fédération n’est pas disponible.
- Fonctionnalités supplémentaires (par exemple, [Azure AD DS](/azure/active-directory-domain-services/tutorial-configure-password-hash-sync)) et services de sécurité (par exemple, [informations d’identification divulguées](/azure/active-directory/reports-monitoring/concept-risk-events#leaked-credentials))
- Prise en charge des services dans Azure qui ne comprennent pas l’authentification fédérée (par exemple, [Azure Files](/azure/storage/files/storage-files-active-directory-overview)).

J’accompagne souvent les clients dans le flux d’authentification client pour clarifier certaines idées fausses. Le résultat ressemble à l’image ci-dessous, ce qui n’est pas aussi bon que le processus interactif d’y arriver.

![Exemple de conversation de tableau blanc.](../media/solutions-architecture-center/identity-beyond-whiteboard-example.png)

Ce type de dessin de tableau blanc illustre l’endroit où les stratégies de sécurité sont appliquées dans le flux d’une demande d’authentification. Dans cet exemple, les stratégies appliquées par le biais d’Active Directory Federation Service (AD FS) sont appliquées à la première demande de service, mais pas aux demandes de service suivantes. Il s’agit au moins d’une raison de déplacer autant que possible les contrôles de sécurité vers le cloud.

Nous avons poursuivi le rêve de l’authentification [unique](/azure/active-directory/manage-apps/what-is-single-sign-on) (SSO) depuis aussi longtemps que je me souviens. Certains clients pensent qu’ils peuvent y parvenir en choisissant le fournisseur de fédération (STS) « approprié ». Azure AD peut aider considérablement à activer les fonctionnalités [d’authentification](/azure/active-directory/manage-apps/plan-sso-deployment) unique, mais aucun STS n’est magique. Il existe trop de méthodes d’authentification « héritées » qui sont toujours utilisées pour les applications critiques. L’extension de Azure AD avec [des solutions partenaires](/azure/active-directory/saas-apps/tutorial-list) peut répondre à un grand nombre de ces scénarios. L’authentification unique est une stratégie et un parcours. Vous ne pouvez pas y arriver sans passer aux [normes pour les applications](/azure/active-directory/develop/v2-app-types). Cette rubrique est liée à un parcours vers l’authentification [sans mot de passe](/azure/active-directory/authentication/concept-authentication-passwordless) , qui n’a pas non plus de réponse magique.

[L’authentification multifacteur](/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) est essentielle aujourd’hui ([ici](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984) pour plus d’informations). Ajoutez-y [l’analytique du comportement des utilisateurs](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) et vous disposez d’une solution qui empêche les cyberattaques les plus courantes. Même les services grand public sont en train de passer à l’authentification multifacteur. Pourtant, je rencontre toujours de nombreux clients qui ne veulent pas passer à des approches [d’authentification modernes](../enterprise/hybrid-modern-auth-overview.md) . Le plus grand argument que j’entends est qu’il aura un impact sur les utilisateurs et les applications héritées. Parfois, un bon coup de pied peut aider les clients à avancer - Exchange Online [changements annoncés](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-auth-and-exchange-online-february-2020-update/ba-p/1191282). De nombreux [rapports](/azure/active-directory/fundamentals/concept-fundamentals-block-legacy-authentication) Azure AD sont désormais disponibles pour aider les clients à effectuer cette transition.

### <a name="authorization"></a>Autorisation

Par [Wikipédia](https://en.wikipedia.org/wiki/Authorization), « autoriser » consiste à définir une stratégie d’accès. De nombreuses personnes y voient la possibilité de définir des contrôles d’accès à un objet (fichier, service, etc.). Dans le monde actuel des cybermenaces, ce concept évolue rapidement vers une stratégie dynamique qui peut réagir à différents vecteurs de menace et ajuster rapidement les contrôles d’accès en réponse à ces derniers. Par exemple, si j’accède à mon compte bancaire à partir d’un emplacement inhabituel, j’obtiens des étapes de confirmation supplémentaires. Pour y parvenir, nous devons prendre en compte non seulement la stratégie elle-même, mais aussi l’écosystème des méthodologies de détection des menaces et de corrélation des signaux.

Le moteur de stratégie de Azure AD est implémenté à l’aide de [stratégies d’accès conditionnel](/azure/active-directory/conditional-access/overview). Ce système dépend des informations d’une variété d’autres systèmes de détection des menaces pour prendre des décisions dynamiques. Une vue simple ressemble à l’illustration suivante :

![Moteur de stratégie dans Azure AD.](../media/solutions-architecture-center/identity-and-beyond-illustration-3.png)

La combinaison de tous ces signaux permet des stratégies dynamiques comme celles-ci :

- Si une menace est détectée sur votre appareil, votre accès aux données sera réduit au web uniquement sans possibilité de téléchargement.
- Si vous téléchargez un volume de données anormalement élevé, tout ce que vous téléchargez est chiffré et restreint.
- Si vous accédez à un service à partir d’un appareil non managé, vous êtes bloqué contre les données hautement sensibles, mais vous êtes autorisé à accéder à des données non restreintes sans pouvoir les copier vers un autre emplacement.

Si vous êtes d’accord avec cette définition étendue de l’autorisation, vous devez implémenter des solutions supplémentaires. Les solutions que vous implémentez dépendent de la dynamique souhaitée pour la stratégie et des menaces que vous souhaitez hiérarchiser. Voici quelques exemples de ces systèmes :

- [Azure AD Identity Protection](/azure/active-directory/identity-protection/)
- [Microsoft Defender pour l’identité](/azure-advanced-threat-protection/)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Microsoft Defender pour Office 365](../security/office-365-security/defender-for-office-365.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) (applications Defender pour le cloud)
- [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md)
- [Microsoft Intune](/mem/intune/)
- [Microsoft Purview Information Protection](../compliance/information-protection.md)
- [Microsoft Sentinel](/azure/sentinel/)

Bien sûr, en plus de Azure AD, différents services et applications ont leurs propres modèles d’autorisation spécifiques. Certains d’entre eux sont abordés plus loin dans la section délégation.

### <a name="audit"></a>Audit

Azure AD dispose de fonctionnalités [d’audit et de création de rapports](/azure/active-directory/reports-monitoring/) détaillées. Toutefois, il ne s’agit généralement pas de la seule source d’informations nécessaire pour prendre des décisions en matière de sécurité. Pour plus d’informations à ce sujet, consultez la section délégation.

## <a name="theres-no-exchange"></a>Il n’y a pas de Exchange

Ne paniquez pas ! Cela ne signifie pas Exchange est déprécié (ou SharePoint, etc.). Il s’agit toujours d’un service de base. Ce que je veux dire, c’est que, depuis un certain temps, les fournisseurs de technologies ont été la transition des expériences utilisateur (UX) pour englober les composants de plusieurs services. Dans Microsoft 365, un exemple simple est « [pièces jointes modernes](https://support.office.com/article/Attach-files-or-insert-pictures-in-Outlook-email-messages-BDFAFEF5-792A-42B1-9A7B-84512D7DE7FC) » où les pièces jointes à l’e-mail sont stockées dans SharePoint Online ou OneDrive Entreprise.

![Attachement d’un fichier à un e-mail.](../media/solutions-architecture-center/modern-attachments.png)

En examinant le client Outlook, vous pouvez voir de nombreux services « connectés » dans le cadre de cette expérience, pas seulement Exchange. Cela inclut les groupes Azure AD, Recherche Microsoft, Applications, Profil, conformité et Office 365.

![Outlook interface avec des légendes.](../media/solutions-architecture-center/identity-and-beyond-conceptual-screenshot.png)

Découvrez [Infrastructure Microsoft Fluid](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-ignite-blog-microsoft-fluid-framework-preview/ba-p/978268) pour obtenir un aperçu des fonctionnalités à venir. En préversion maintenant, je peux lire et répondre à Teams conversations directement dans Outlook. En fait, le [client Teams](https://products.office.com/microsoft-teams/download-app) est l’un des exemples les plus importants de cette stratégie.

Dans l’ensemble, il est de plus en plus difficile de tracer une ligne claire entre Office 365 et d’autres services dans les clouds Microsoft. Je le considère comme un grand avantage pour les clients, car ils peuvent bénéficier de l’innovation totale dans tout ce que nous faisons, même s’ils utilisent un composant. Assez cool et a des implications de grande portée pour de nombreux clients.

Aujourd’hui, je trouve que de nombreux groupes informatiques clients sont structurés autour de « produits ». C’est logique pour un monde local, car vous avez besoin d’un expert pour chaque produit spécifique. Toutefois, je suis totalement heureux de ne plus avoir à déboguer une base de données Active Directory ou Exchange, car ces services ont été déplacés vers le cloud. L’automatisation (qui est le type de cloud) supprime certains travaux manuels répétitifs (regardez ce qui est arrivé aux usines). Toutefois, ces exigences sont remplacées par des exigences plus complexes pour comprendre l’interaction entre services, l’impact, les besoins de l’entreprise, etc. Si vous êtes prêt à [apprendre](/learn/), la transformation cloud offre de grandes opportunités. Avant de passer à la technologie, je parle souvent aux clients de la gestion des changements dans les compétences informatiques et les structures d’équipe.

À tous les SharePoint fans et développeurs, arrêtez de demander « Comment puis-je faire XYZ dans SharePoint en ligne ? » Utilisez [Power Automate](/power-automate/) (ou Flow) pour le flux de travail, il s’agit d’une plateforme beaucoup plus puissante. Utilisez [Azure Bot Framework](/azure/bot-service/) pour créer une meilleure expérience utilisateur pour votre liste d’éléments de 500 K. Commencez à utiliser [Microsoft Graph](https://developer.microsoft.com/graph/) au lieu de CSOM. [Microsoft Teams](/MicrosoftTeams/Teams-overview) comprend SharePoint mais aussi un monde plus. Il existe de nombreux autres exemples que je peux lister. Il y a un univers vaste et merveilleux. Ouvrez la porte et [commencez à explorer]().

L’autre impact courant se trouve dans le domaine de la conformité. Cette approche inter-services semble complètement confondre de nombreuses stratégies de conformité. Je continue à voir les organisations qui déclarent : « Je dois journaliser toutes les communications par e-mail vers un système eDiscovery ». Qu’est-ce que cela signifie vraiment lorsque l’e-mail n’est plus seulement un e-mail, mais une fenêtre dans d’autres services ? Office 365 a une approche globale de [la conformité](../compliance/index.yml), mais les changements de personnes et de processus sont souvent beaucoup plus difficiles que la technologie.

Il y a beaucoup d’autres personnes et des implications de processus. À mon avis, il s’agit d’un domaine critique et sous-abordé. Peut-être plus dans un autre article.

## <a name="tenant-structure-options"></a>Options de structure de locataire

### <a name="single-tenant-vs-multi-tenant"></a>Client unique et multilocataire

En général, la plupart des clients ne doivent avoir qu’un seul locataire de production. Il existe de nombreuses raisons pour lesquelles plusieurs locataires sont difficiles (donnez-lui une [recherche Bing](https://www.bing.com/search?q=office%20365%20multiple%20tenants)) ou lisez ce [livre blanc](https://aka.ms/multi-tenant-user). Dans le même temps, de nombreux clients d’entreprise avec qui je travaille ont un autre (petit) locataire pour l’apprentissage informatique, les tests et l’expérimentation. L’accès Azure interlocataire est facilité avec [Azure Lighthouse](https://azure.microsoft.com/services/azure-lighthouse/). Office 365 et de nombreux autres services SaaS ont des limites pour les scénarios interlocataires. Il y a beaucoup à prendre en compte dans Azure AD scénarios [B2B](/azure/active-directory/b2b/what-is-b2b).

De nombreux clients se retrouvent avec plusieurs locataires de production après une fusion et une acquisition (M&A) et souhaitent consolider. Aujourd’hui, ce n’est pas simple et nécessiterait Microsoft Consulting Services (MCS) ou un partenaire plus des logiciels tiers. Des travaux d’ingénierie sont en cours pour résoudre différents scénarios avec des clients multilocataires à l’avenir.

Certains clients choisissent d’utiliser plusieurs locataires. Il devrait s’agir d’une décision très prudente et presque toujours pilotée par des raisons professionnelles! Voici quelques exemples :

- Structure d’entreprise de type holding où il n’est pas nécessaire de collaborer facilement entre différentes entités et où il existe de solides besoins d’isolation et d’administration.
- Après une acquisition, une décision d’entreprise est prise pour séparer deux entités.
- Simulation de l’environnement d’un client qui ne modifie pas l’environnement de production du client.
- Développement de logiciels pour les clients.

Dans ces scénarios multilocataires, les clients souhaitent souvent conserver une configuration identique entre les locataires, ou signaler les modifications de configuration et les dérives. Cela signifie souvent passer de modifications manuelles à la configuration en tant que code. Le support Microsoft Premiere propose un atelier pour ces types d’exigences en fonction de cette adresse IP publique : <https://Microsoft365dsc.com>.

### <a name="multi-geo"></a>Multi-Géo

À [multigéographique](../enterprise/microsoft-365-multi-geo.md) ou non à multigéographique, c’est la question. Avec Office 365 multigéographique, vous pouvez provisionner et stocker des données au repos dans les emplacements géographiques que vous avez choisis pour répondre aux exigences de [résidence des données](../enterprise/o365-data-locations.md). Il existe de nombreuses idées fausses sur cette fonctionnalité. Gardez les éléments suivants à l’esprit :

- Il ne fournit pas d’avantages en matière de performances. Cela pourrait aggraver les performances si la [conception du réseau](https://aka.ms/office365networking) n’est pas correcte. Obtenez les appareils « proches » du réseau Microsoft, pas nécessairement de vos données.
- Il ne s’agit pas d’une solution pour [la conformité au RGPD](https://www.microsoft.com/trust-center/privacy/gdpr-overview). Le RGPD ne se concentre pas sur la souveraineté des données ou les emplacements de stockage. Il existe d’autres frameworks de conformité pour cela.
- Il ne résout pas les obstacles à la délégation de l’administration (voir ci-dessous) ou [à l’information](../compliance/information-barriers.md).
- Il n’est pas le même que le multilocataire et nécessite des workflows [d’approvisionnement d’utilisateurs](https://github.com/MicrosoftDocs/azure-docs-pr/blob/master/articles/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation.md) supplémentaires.
- Il ne [déplace pas votre locataire](../enterprise/moving-data-to-new-datacenter-geos.md) (votre Azure AD) vers une autre zone géographique.

## <a name="delegation-of-administration"></a>Délégation d’administration

Dans la plupart des grandes organisations, la séparation des tâches et du contrôle d’accès en fonction du rôle (RBAC) est une réalité nécessaire. Je vais m’excuser à l’avance. Ce n’est pas aussi simple que certains clients le souhaitent. Les exigences relatives aux clients, juridiques, de conformité et autres sont différentes et parfois conflictuelles dans le monde entier. La simplicité et la flexibilité sont souvent de part et d’autre. Ne vous méprenez pas, nous pouvons faire un meilleur travail à ce sujet. Des améliorations significatives ont été (et seront) apportées au fil du temps. Visitez votre [Centre technologique Microsoft](https://www.microsoft.com/mtc) local pour découvrir le modèle qui répond aux besoins de votre entreprise sans lire la documentation 379230 ! Ici, je vais me concentrer sur ce que vous devriez penser et non pas pourquoi c’est de cette façon. Voici cinq domaines différents à planifier et quelques-unes des questions courantes que j’ai rencontrées.

### <a name="azure-ad-and-microsoft-365-admin-centers"></a>centres d’administration Azure AD et Microsoft 365

La liste des [rôles intégrés](/azure/active-directory/roles/permissions-reference) est longue et croissante. Chaque rôle se compose d’une liste d’autorisations de rôle regroupées pour permettre l’exécution d’actions spécifiques. Vous pouvez voir ces autorisations sous l’onglet « Description » à l’intérieur de chaque rôle. Vous pouvez également voir une version plus lisible de ces éléments dans le centre Administration Microsoft 365. Les définitions des rôles intégrés ne peuvent pas être modifiées. Je les regroupe généralement en trois catégories :

- **Administrateur général** : ce rôle « tout puissant » doit être [hautement protégé](../enterprise/protect-your-global-administrator-accounts.md) comme vous le feriez dans d’autres systèmes. Les recommandations classiques sont les suivantes : aucune affectation permanente et utilisation de Azure AD Privileged Identity Management (PIM), une authentification forte, etc. Il est intéressant de noter que ce rôle ne vous donne pas accès à tout par défaut. En règle générale, je vois une confusion au sujet de l’accès à la conformité et de l’accès Azure, dont nous discuterons plus loin. Toutefois, ce rôle peut toujours attribuer l’accès à d’autres services dans le locataire.
- **Administrateurs de services spécifiques** : certains services (Exchange, SharePoint, Power BI, et ainsi de suite) utilisent des rôles d’administration de haut niveau à partir de Azure AD. Cela n’est pas cohérent entre tous les services et d’autres rôles spécifiques au service sont abordés ultérieurement.
- **Fonctionnel** : Il existe une longue liste (et croissante) de rôles axés sur des opérations spécifiques (inviteur invité, etc.). Régulièrement, un plus grand nombre d’entre eux sont ajoutés en fonction des besoins des clients.

Il n’est pas possible de déléguer tout (bien que l’écart diminue), ce qui signifie que le rôle d’administrateur général doit parfois être utilisé. La configuration en tant que code et l’automatisation doivent être prises en compte au lieu de l’appartenance des personnes à ce rôle.

**Remarque** : l’Centre d'administration Microsoft 365 dispose d’une interface plus conviviale, mais possède un sous-ensemble de fonctionnalités par rapport à l’expérience d’administrateur Azure AD. Les deux portails utilisent les mêmes rôles Azure AD, de sorte que les modifications se produisent au même endroit. Conseil : si vous souhaitez une interface utilisateur d’administration axée sur la gestion des identités sans tout le courrier pêle-mêle Azure, utilisez <https://aad.portal.azure.com>.

Qu’y a-t-il dans le nom ? Ne faites pas d’hypothèses à partir du nom du rôle. La langue n’est pas un outil très précis. L’objectif doit être de définir les opérations qui doivent être déléguées avant d’examiner les rôles nécessaires. L’ajout d’une personne au rôle « Lecteur de sécurité » ne lui permet pas d’afficher les paramètres de sécurité dans tous les domaines.

La possibilité de créer des [rôles personnalisés](/azure/active-directory/users-groups-roles/roles-custom-overview) est une question courante. Ce nombre est limité dans Azure AD aujourd’hui (voir ci-dessous), mais il augmentera au fil du temps. Je pense que ces paramètres s’appliquent aux fonctions dans Azure AD et peuvent ne pas s’étendre sur « down » le modèle de hiérarchie (décrit ci-dessus). Chaque fois que je traite de « personnalisé », j’ai tendance à revenir à mon principal de « simple is better ».

Une autre question courante est la possibilité d’étendre les rôles à un sous-ensemble d’un répertoire. Un exemple est semblable à « Administrateur du support technique pour les utilisateurs dans l’UE uniquement ». [Les unités administratives](/azure/active-directory/users-groups-roles/directory-administrative-units) (AU) sont destinées à résoudre ce problème. Comme ci-dessus, je les considère comme applicables aux fonctions dans Azure AD et peuvent ne pas s’étendre sur « down ». Bien sûr, certains rôles n’ont pas de sens pour l’étendue (administrateurs généraux, administrateurs de services, etc.).

Aujourd’hui, tous ces rôles nécessitent une appartenance directe (ou une attribution dynamique si vous utilisez [Azure AD PIM](/azure/active-directory/privileged-identity-management/)). Cela signifie que les clients doivent les gérer directement dans Azure AD et ceux-ci ne peuvent pas être basés sur une appartenance à un groupe de sécurité. Je ne suis pas fan de la création de scripts pour les gérer, car il aurait besoin de s’exécuter avec des droits élevés. Je recommande généralement l’intégration d’API à des systèmes de processus tels que ServiceNow ou à l’aide d’outils de gouvernance de partenaires tels que Saviynt. Des travaux d’ingénierie sont en cours pour résoudre ce problème au fil du temps.

J’ai mentionné [Azure AD PIM](/azure/active-directory/privileged-identity-management/) plusieurs fois. Il existe une solution Microsoft Identity Manager (MIM) [Privileged Access Management](/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) (PAM) correspondante pour les contrôles locaux. Vous pouvez également examiner les stations de [travail à accès privilégié](/windows-server/identity/securing-privileged-access/privileged-access-workstations) (PAW) et [Azure AD gouvernance des identités](/azure/active-directory/governance/identity-governance-overview). Il existe également différents outils tiers, qui peuvent activer l’élévation de rôle juste-à-temps, juste-à-temps et dynamique. Cela fait généralement partie d’une discussion plus large sur la sécurisation d’un environnement.

Parfois, des scénarios appellent l’ajout d’un utilisateur externe à un rôle (voir la section multilocataire, ci-dessus). Ça marche très bien. [Azure AD B2B](/azure/active-directory/b2b/) est un autre sujet volumineux et amusant à parcourir pour les clients, peut-être dans un autre article.

### <a name="security-and-compliance-center-scc"></a>Centre de sécurité et de conformité (SCC)

[Les autorisations dans le Centre de sécurité & conformité Office 365](../security/office-365-security/permissions-in-the-security-and-compliance-center.md) sont une collection de « groupes de rôles », qui sont distincts des rôles Azure AD. Cela peut prêter à confusion, car certains de ces groupes de rôles portent le même nom que Azure AD rôles (par exemple, Lecteur sécurité), mais ils peuvent avoir des appartenances différentes. Je préfère l’utilisation de rôles Azure AD. Chaque groupe de rôles se compose d’un ou plusieurs « rôles » (voir ce que je veux dire sur la réutilisation du même mot ?) et ont des membres de Azure AD, qui sont des objets activés par e-mail. En outre, vous pouvez créer un groupe de rôles portant le même nom qu’un rôle, qui peut ou non contenir ce rôle (évitez cette confusion).

En un sens, il s’agit d’une évolution du modèle de groupes de rôles Exchange. Toutefois, Exchange Online a sa propre interface [de gestion de groupe de rôles](/exchange/permissions-exo). Certains groupes de rôles dans Exchange Online sont verrouillés et gérés à partir de Azure AD ou du Centre de sécurité & conformité, mais d’autres peuvent avoir les mêmes noms ou des noms similaires et sont gérés dans Exchange Online (ce qui ajoute à la confusion). Je vous recommande d’éviter d’utiliser l’interface utilisateur Exchange Online, sauf si vous avez besoin d’étendues pour la gestion Exchange.

Vous ne pouvez pas créer de rôles personnalisés. Les rôles sont définis par les services créés par Microsoft et augmenteront à mesure que de nouveaux services seront introduits. Ce concept est similaire aux [rôles définis par les applications](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) dans Azure AD. Lorsque de nouveaux services sont activés, de nouveaux groupes de rôles doivent souvent être créés pour accorder ou déléguer l’accès à ces derniers (par exemple, [la gestion des risques internes](../compliance/insider-risk-management-configure.md).

Ces groupes de rôles nécessitent également une appartenance directe et ne peuvent pas contenir de groupes Azure AD. Malheureusement, aujourd’hui, ces groupes de rôles ne sont pas pris en charge par Azure AD PIM. Comme Azure AD rôles, j’ai tendance à recommander la gestion de ces rôles par le biais d’API ou d’un produit de gouvernance de partenaire comme Saviynt ou d’autres.

La sécurité & les rôles du Centre de conformité s’étendent sur Microsoft 365 et vous ne pouvez pas étendre ces groupes de rôles à un sous-ensemble de l’environnement (comme vous le pouvez avec les unités administratives dans Azure AD). De nombreux clients demandent comment ils peuvent subdéléguer. Par exemple, « créez une stratégie DLP uniquement pour les utilisateurs de l’UE ». Aujourd’hui, si vous avez des droits sur une fonction spécifique dans le Centre de sécurité & conformité, vous disposez de droits sur tout ce qui est couvert par cette fonction dans le locataire. Toutefois, de nombreuses stratégies ont des fonctionnalités pour cibler un sous-ensemble de l’environnement (par exemple, « rendre ces [étiquettes](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) disponibles uniquement pour ces utilisateurs »). Une gouvernance et une communication appropriées sont un composant clé pour éviter les conflits. Certains clients choisissent d’implémenter une approche de « configuration en tant que code » pour traiter la sous-délégation dans le Centre de sécurité & conformité. Certains services spécifiques prennent en charge la sous-délégation (voir ci-dessous).

Il est important de noter que les contrôles actuellement gérés via le Centre de sécurité & conformité (protection.office.com) sont en cours de migration vers deux portails d’administration distincts : security.microsoft.com et compliance.microsoft.com. Le changement est la seule constante!

### <a name="service-specific"></a>Spécifique au service

Comme indiqué précédemment, de nombreux clients cherchent à obtenir un modèle de délégation plus précis. Exemple courant : « Gérer le service XYZ uniquement pour les utilisateurs et les emplacements de la division X » (ou une autre dimension). La possibilité d’effectuer cette opération dépend de chaque service et n’est pas cohérente entre les services et les fonctionnalités. En outre, chaque service peut avoir un modèle RBAC distinct et unique. Au lieu de discuter de tous ces éléments (cela prendra toujours), j’ajoute des liens pertinents pour chaque service. Il ne s’agit pas d’une liste complète, mais elle vous permettra de commencer.

- **Exchange Online** - (/exchange/permissions-exo/permissions-exo)
- **SharePoint Online** - (/sharepoint/manage-site-collection-administrators)
- **Microsoft Teams** - (/microsoftteams/itadmin-readiness)
- **eDiscovery** - (.. /compliance/index.yml)
  - **Filtrage des autorisations** - (.. /compliance/index.yml)
  - **Limites de conformité** - (.. /compliance/set-up-compliance-boundaries.md)
  - **Advanced eDiscovery** - (.. /compliance/overview-ediscovery-20.md)
- **Yammer** - (/yammer/manage-yammer-users/manage-yammer-admins)
- **Multigéographique** - (.. /enterprise/add-a-sharepoint-geo-admin.md)
- **Dynamics 365** – (/dynamics365/)

  Remarque : ce lien est à la racine de la documentation. Il existe plusieurs types de services avec des variantes dans le modèle d’administration/délégation.

- **Power Platform** - (/power-platform/admin/admin-documentation)
  - **Power Apps** - (/power-platform/admin/wp-security)

    Remarque : il existe plusieurs types avec des variantes dans les modèles d’administration/délégation.

  - **Power Automate** - (/power-automate/environments-overview-admin)
  - **Power BI** - (/power-bi/service-admin-governance)

    Remarque : la sécurité et la délégation de la plateforme de données (qui Power BI est un composant) est un domaine complexe.

- **MEM/Intune** - (/mem/intune/fundamentals/role-based-access-control)
- **Microsoft Defender pour point de terminaison** - (/windows/security/threat-protection/microsoft-defender-atp/user-roles)
- **Microsoft 365 Defender** - (.. /security/defender/m365d-permissions.md)
- **Microsoft Defender for Cloud Apps** - (/cloud-app-security/manage-admins)
- **Stream** - (/stream/assign-administrator-user-role)
- **Obstacles à l’information** - (.. /compliance/information-barriers.md)

### <a name="activity-logs"></a>Journaux d’activité

Office 365 dispose d’un [journal d’audit unifié](../compliance/search-the-audit-log-in-security-and-compliance.md). Il s’agit d’un [journal très détaillé](/office/office-365-management-api/office-365-management-activity-api-schema), mais ne lisez pas trop dans le nom. Il peut ne pas contenir tout ce dont vous avez besoin ou tout ce dont vous avez besoin pour vos besoins en matière de sécurité et de conformité. En outre, certains clients sont vraiment intéressés par [l’audit avancé](../compliance/advanced-audit.md).

Voici quelques exemples de journaux d’activité Microsoft 365 accessibles via d’autres API :

- [Azure AD](/azure/azure-monitor/platform/diagnostic-settings) (activités non liées à Office 365)
- [Exchange suivi des messages](/powershell/module/exchange/get-messagetrace)
- Systèmes UEBA/menaces abordés ci-dessus (par exemple, Azure AD Identity Protection, Microsoft Defender for Cloud Apps, Microsoft Defender pour point de terminaison, et ainsi de suite)
- [Microsoft Purview Information Protection](../compliance/data-classification-activity-explorer.md)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/api-power-bi)
- [Microsoft Graph](https://graph.microsoft.com)

Il est important d’identifier d’abord toutes les sources de journaux nécessaires à un programme de sécurité et de conformité. Notez également que les différents journaux d’activité ont des limites de rétention en ligne différentes.

Du point de vue de la délégation d’administration, la plupart des journaux d’activité Microsoft 365 n’ont pas de modèle RBAC intégré. Si vous avez l’autorisation d’afficher un journal, vous pouvez voir tout ce qu’il contient. Un exemple courant d’exigence du client est : « Je veux pouvoir interroger l’activité uniquement pour les utilisateurs de l’UE » (ou une autre dimension). Pour répondre à cette exigence, nous devons transférer les journaux vers un autre service. Dans le cloud Microsoft, nous vous recommandons de le transférer vers [Microsoft Sentinel](/azure/sentinel/overview) ou [Log Analytics](/azure/azure-monitor/learn/quick-create-workspace).

Diagramme de haut niveau :

![diagramme des sources de journaux pour un programme de sécurité et de conformité.](../media/solutions-architecture-center/identity-beyond-illustration-4.png)

Le diagramme ci-dessus représente les fonctionnalités intégrées pour envoyer des journaux à Event Hub et/ou stockage Azure et/ou Azure Log Analytics. Tous les systèmes n’incluent pas encore cette fonctionnalité. Mais il existe d’autres approches pour envoyer ces journaux au même référentiel. Par exemple, consultez [Protection de vos Teams avec Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/protecting-your-teams-with-azure-sentinel/ba-p/1265761).

La combinaison de tous les journaux dans un seul emplacement de stockage offre un avantage supplémentaire, comme les corrélations croisées, les temps de rétention personnalisés, l’augmentation des données nécessaires pour prendre en charge le modèle RBAC, etc. Une fois que les données se trouvent dans ce système de stockage, vous pouvez créer un tableau de bord Power BI (ou un autre type de visualisation) avec un modèle RBAC approprié.

Les journaux d’activité ne doivent pas nécessairement être dirigés vers un seul emplacement. Il peut également être utile d’intégrer [Office 365 Journaux à Microsoft Defender for Cloud Apps](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) ou à un modèle RBAC personnalisé dans [Power BI](../admin/usage-analytics/usage-analytics.md). Les différents référentiels ont des avantages et des audiences différents.

Il est important de mentionner qu’il existe un système d’analyse intégré très riche pour la sécurité, les menaces, les vulnérabilités, et ainsi de suite dans un service appelé [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md).

De nombreux grands clients souhaitent transférer ces données de journal vers un système tiers (par exemple, SIEM). Il existe différentes approches pour cela, mais en général[, Azure Event Hub](/azure/azure-monitor/platform/stream-monitoring-data-event-hubs) et [Graph](/graph/security-integration) sont de bons points de départ.

### <a name="azure"></a>Azure

On me demande souvent s’il existe un moyen de séparer les rôles à privilèges élevés entre Azure AD, Azure et SaaS (par exemple, Administrateur général pour Office 365 mais pas Azure).  Pas vraiment.  L’architecture mutualisée est nécessaire si une séparation administrative complète est requise, mais cela ajoute une [complexité](https://aka.ms/multi-tenant-user) significative (voir ci-dessus). Tous ces services font partie de la même limite de sécurité/identité (consultez le modèle de hiérarchie ci-dessus).

Il est important de comprendre les relations entre différents services dans le même locataire. Je travaille avec de nombreux clients qui créent des solutions métier qui couvrent Azure, Office 365 et Power Platform (et souvent aussi des services cloud locaux et tiers). Un exemple courant :

1. Je souhaite collaborer sur un ensemble de documents/images/etc. (Office 365)
2. Envoyer chacun d’eux par le biais d’un processus d’approbation (Power Platform)
3. Une fois tous les composants approuvés, assemblez-les dans un ou plusieurs livrables (Azure) [Microsoft API Graph](/azure/active-directory/develop/microsoft-graph-intro) est votre meilleur ami pour ces composants.  Pas impossible, mais beaucoup plus complexe pour concevoir une solution couvrant [plusieurs locataires](/azure/active-directory/develop/single-and-multi-tenant-apps).

Azure Role-Based Access Control (RBAC) permet une gestion affinée des accès pour Azure. Avec RBAC, vous pouvez gérer l’accès aux ressources en accordant aux utilisateurs le moins d’autorisations nécessaires pour effectuer leurs travaux. Les détails sont hors de portée pour ce document, mais pour plus d’informations sur RBAC, consultez [Qu’est-ce que le contrôle d’accès en fonction du rôle (RBAC) dans Azure ?](/azure/role-based-access-control/overview) Le contrôle d’accès en fonction du rôle (RBAC) est important, mais seulement une partie des considérations de gouvernance pour Azure. [Cloud Adoption Framework](/azure/cloud-adoption-framework/govern/) est un excellent point de départ pour en savoir plus. J’aime la façon dont mon ami [, Andres Ravinet](https://www.linkedin.com/in/andres-ravinet/), guide les clients pas à pas dans différents composants pour décider de l’approche. Une vue générale pour différents éléments (pas aussi bon que le processus d’obtention du modèle client réel) est semblable à ceci :

![Vue générale des composants Azure pour l’administration déléguée.](../media/solutions-architecture-center/identity-beyond-illustration-5.png)

Comme vous pouvez le voir dans l’image ci-dessus, de nombreux autres services doivent être considérés comme faisant partie de la conception (par exemple, [Azure Policies](/azure/governance/policy/overview), [Azure Blueprints](/azure/governance/blueprints/overview), [Groupes d’administration](/azure/governance/management-groups/), etc.).

## <a name="conclusion"></a>Conclusion

Commencé comme un résumé court, a fini par plus longtemps que je m’y attendais.  J’espère que vous êtes maintenant prêt à vous lancer dans la création d’un modèle de délégation pour votre organisation.  Cette conversation est très courante avec les clients. Il n’existe aucun modèle qui fonctionne pour tout le monde. En attente de quelques améliorations planifiées de l’ingénierie Microsoft avant de documenter les modèles courants que nous voyons parmi les clients. En attendant, vous pouvez collaborer avec votre équipe de compte Microsoft pour organiser une visite au [Centre technologique Microsoft](https://www.microsoft.com/mtc) le plus proche.  On se voit là-bas !
