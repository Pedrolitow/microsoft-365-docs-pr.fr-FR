---
title: Pile de protection pas à pas contre les menaces dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/05/2021
ms.reviewer: gigarrub
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
description: Suivez le chemin d’un message entrant via la pile de filtrage des menaces dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 96e7fb9a4e774b51b1d2138cd72ea468bc23ee7b
ms.sourcegitcommit: e6595be36bbaba244439bd59dbae935e2b258ded
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2022
ms.locfileid: "67450144"
---
# <a name="step-by-step-threat-protection-in-microsoft-defender-for-office-365"></a>Protection contre les menaces étape par étape dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

La pile de protection ou de filtrage Microsoft Defender pour Office 365 peut être divisée en 4 phases, comme dans cet article. En règle générale, le courrier entrant passe par toutes ces phases avant la remise, mais le chemin d’accès réel est soumis à la configuration Defender pour Office 365 d’une organisation.

> [!TIP]
> Restez à l’écoute jusqu’à la fin de cet article pour obtenir un graphique *unifié* des 4 phases de protection Defender pour Office 365!

## <a name="phase-1---edge-protection"></a>Phase 1 - Edge Protection

Malheureusement, les blocs Edge qui étaient autrefois *critiques* sont maintenant relativement simples pour les mauvais acteurs à surmonter. Au fil du temps, moins de trafic est bloqué ici, mais il reste une partie importante de la pile.  

Les blocs edge sont conçus pour être automatiques. En cas de faux positifs, les expéditeurs sont avertis et informés de la façon de résoudre leur problème. Les connecteurs de partenaires approuvés ayant une réputation limitée peuvent garantir la livrabilité, ou des remplacements temporaires peuvent être mis en place lors de l’intégration de nouveaux points de terminaison.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png" alt-text="Filtrage de phase 1 dans Defender pour Office 365" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png":::

1. **La limitation du réseau** protège Office 365'infrastructure et les clients contre les attaques par déni de service (DOS) en limitant le nombre de messages qui peuvent être envoyés par un ensemble spécifique d’infrastructure.

2. **La réputation et la limitation** ip bloquent l’envoi de messages à partir d’adresses IP de connexion incorrectes connues. Si une adresse IP spécifique envoie de nombreux messages dans un court laps de temps, elles sont limitées.

3. **La réputation du domaine** bloque les messages envoyés à partir d’un domaine incorrect connu.

4. **Le filtrage Edge basé sur l’annuaire** bloque les tentatives de recherche des informations d’annuaire d’une organisation via SMTP.

5. **La détection de la rétrodiffusion** empêche l’attaque d’une organisation par le biais de rapports de non-remise (NDR) non valides.

6. **Le filtrage amélioré pour les connecteurs** conserve les informations d’authentification même lorsque le trafic passe par un autre appareil avant d’atteindre Office 365. Cela améliore la précision de la pile de filtrage, notamment le clustering heuristique, l’usurpation d’identité et les modèles Machine Learning anti-hameçonnage, même dans des scénarios de routage complexes ou hybrides.

## <a name="phase-2---sender-intelligence"></a>Phase 2 - Intelligence de l’expéditeur

Les fonctionnalités de l’intelligence de l’expéditeur sont essentielles pour intercepter le courrier indésirable, le courrier en bloc, l’emprunt d’identité et les messages d’usurpation d’identité non autorisés, et également prendre en compte la détection de hameçonnage. La plupart de ces fonctionnalités sont configurables individuellement.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png" alt-text="La phase 2 du filtrage dans Defender pour Office 365 est l’intelligence de l’expéditeur" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png":::

1. Les déclencheurs et alertes de **détection de compromission** de compte sont déclenchés lorsqu’un compte a un comportement anormal, cohérent avec la compromission. Dans certains cas, le compte d’utilisateur est bloqué et empêché d’envoyer d’autres messages électroniques tant que le problème n’est pas résolu par l’équipe des opérations de sécurité d’une organisation.

2. **Email l’authentification** implique à la fois des méthodes configurées par le client et des méthodes configurées dans le cloud, afin de s’assurer que les expéditeurs sont des expéditeurs autorisés et authentiques. Ces méthodes résistent à l’usurpation d’identité.
    - **SPF** peut rejeter des messages basés sur des enregistrements TXT DNS qui répertorient les adresses IP et les serveurs autorisés à envoyer des messages au nom de l’organisation.
    - **DKIM** fournit une signature chiffrée qui authentifie l’expéditeur.
    - **DMARC** permet aux administrateurs de marquer SPF et DKIM comme requis dans leur domaine et applique l’alignement entre les résultats de ces deux technologies.
    - **ARC** s’appuie sur DMARC pour utiliser le transfert dans les listes de diffusion lors de l’enregistrement d’une chaîne d’authentification.

3. **L’intelligence par usurpation** d’identité est capable de filtrer celles autorisées à « usurper » (autrement dit, celles qui envoient du courrier pour le compte d’un autre compte ou qui transfèrent une liste de diffusion) à partir d’expéditeurs malveillants qui imitent des domaines externes connus ou organisationnels. Il sépare les courriers légitimes « au nom de » des expéditeurs qui usurpent l’usurpation d’identité pour remettre des messages de courrier indésirable et de hameçonnage.

    **La veille contre l’usurpation d’informations intra-organisationnelle** détecte et bloque les tentatives d’usurpation d’informations à partir d’un domaine au sein de l’organisation.

4. **La veille contre l’usurpation inter-domaines** détecte et bloque les tentatives d’usurpation d’informations à partir d’un domaine extérieur à l’organisation.

5. **Le filtrage en bloc** permet aux administrateurs de configurer un niveau de confiance en bloc (BCL) indiquant si le message a été envoyé à partir d’un expéditeur en bloc. Les administrateurs peuvent utiliser le curseur en bloc dans la stratégie Antispam pour déterminer le niveau de courrier en bloc à traiter comme courrier indésirable.

6. **La veille des boîtes aux lettres** apprend les comportements de messagerie standard de l’utilisateur. Il tire parti du graphique de communication d’un utilisateur pour détecter quand un expéditeur ne semble être qu’une personne avec laquelle l’utilisateur communique généralement, mais qu’il est en fait malveillant. Cette méthode détecte l’emprunt d’identité.

7. **L’emprunt d’identité d’intelligence** de boîte aux lettres active ou désactive les résultats d’emprunt d’identité améliorés en fonction de la carte d’expéditeur individuelle de chaque utilisateur. Quand elle est activée, cette fonctionnalité permet d’identifier l’emprunt d’identité.

8. **L’emprunt d’identité** utilisateur permet à un administrateur de créer une liste de cibles à valeur élevée susceptibles d’être empruntées. Si un message arrive lorsque l’expéditeur semble avoir uniquement le même nom et la même adresse que le compte à valeur élevée protégé, le courrier est marqué ou marqué. (Par exemple, *trα cye@contoso.com* pour *tracye@contoso.com*).

9. **L’emprunt d’identité de domaine** détecte les domaines qui sont similaires au domaine du destinataire et qui tentent de ressembler à un domaine interne. Par exemple, cette emprunt d’identité *tracye@liw α re.com* pour *tracye@litware.com*.

## <a name="phase-3---content-filtering"></a>Phase 3 - Filtrage de contenu

Dans cette phase, la pile de filtrage commence à gérer le contenu spécifique du courrier, y compris ses liens hypertexte et pièces jointes.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png" alt-text="Le filtrage de phase 3 dans MDO est le filtrage de contenu" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png":::

1. **Les règles de transport** (également appelées règles de flux de messagerie ou règles de transport Exchange) permettent à un administrateur d’effectuer un large éventail d’actions lorsqu’un large éventail de conditions sont remplies pour un message. Tous les messages qui transitent par votre organisation sont évalués par rapport aux règles /règles de transport de flux de courrier activées.

2. L’**Antivirus Microsoft Defender** et deux *moteurs antivirus tiers* sont utilisés pour détecter tous les programmes malveillants connus dans les pièces jointes.

3. Les moteurs antivirus sont également utilisés pour taper toutes les pièces jointes de façon à ce que le **blocage de type** puisse bloquer toutes les pièces jointes des types spécifiés par l’administrateur.

4. Chaque fois que Microsoft Defender pour Office 365 détecte une pièce jointe malveillante, le hachage du fichier et un hachage de son contenu actif sont ajoutés à Exchange Online Protection réputation (EOP). **Le blocage de la réputation des pièces jointes** bloque ce fichier sur tous les Office 365 et sur les points de terminaison, via les appels cloud MSAV.

5. La **Mise en cluster heuristique** peut déterminer qu’un fichier est suspect en fonction de l’heuristique de remise. Lorsqu’une pièce jointe suspecte est trouvée, la campagne entière s’interrompt et le fichier est en bac à sable (sandbox). Si le fichier est détecté comme malveillant, l’intégralité de la campagne est bloquée.

6. Les **Modèles d’apprentissage automatique** agissent sur l’en-tête, le contenu du corps et les URL d’un message pour détecter les tentatives de hameçonnage.

7. Microsoft utilise une détermination de la réputation du bac à sable URL ainsi que la réputation d’URL des flux tiers dans le **blocage de la réputation d’URL**, pour bloquer tout message avec une URL malveillante connue.

8. Les **Heuristiques de contenu** peuvent détecter des messages suspects en fonction de la structure et de la fréquence des mots dans le corps du message, à l’aide de modèles d’apprentissage automatique.

9. **Les pièces jointes sécurisées sont des bacs** à sable (sandbox) pour chaque pièce jointe pour Defender pour Office 365 clients, en utilisant l’analyse dynamique pour détecter les menaces jamais vues auparavant.

10. La **Détonation de contenu lié** traite chaque URL liée à un fichier dans un e-mail comme une pièce jointe, la mettant en bac à sable asynchrone au moment de la remise.

11. La **Détonation d’URL** se produit lorsque la technologie anti-hameçonnage en amont trouve qu’un message ou une URL est suspect. La détonation d’URL fait détoner les URL du message au moment de la remise.

## <a name="phase-4---post-delivery-protection"></a>Phase 4 - Protection post-remise

La dernière étape a lieu après la remise du courrier ou des fichiers, en agissant sur le courrier qui se trouve dans différentes boîtes aux lettres et fichiers et liens qui apparaissent dans des clients tels que Microsoft Teams.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png" alt-text="Le filtrage de phase 4 dans Defender pour Office 365 est la protection après remise" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png":::

1. Les **Liens fiables** sont la protection au moment du clic de Defender pour Office 365. Chaque URL de chaque message est encapsulée pour pointer vers les serveurs Microsoft Safe Links. Lorsqu’une URL est cliqué, elle est vérifiée par rapport à la dernière réputation, avant que l’utilisateur soit redirigé vers le site cible. L’URL est en bac à sable de manière asynchrone pour mettre à jour sa réputation.

2. **Le vidage automatique de zéro heure (ZAP) pour le hameçonnage** détecte et neutralise rétroactivement les messages de hameçonnage malveillants qui ont déjà été remis aux boîtes aux lettres Exchange Online.

3. La **Purge automatique zéro heure pour les programmes malveillants** détecte et neutralise les messages de programmes malveillants qui ont déjà été remis dans les boîtes aux lettres Exchange Online.

4. La **Purge automatique zéro heure pour le courrier indésirable** détecte et neutralise de manière rétroactive les messages malveillants de courriers indésirables qui ont déjà été remis dans les boîtes aux lettres Exchange Online.

5. **Les vues de campagne** permettent aux administrateurs de voir la vue d’ensemble d’une attaque, plus rapidement et plus complètement, que n’importe quelle équipe ne pourrait sans automatisation. Microsoft tire parti des grandes quantités de données anti-hameçonnage, anti-spam et anti-programme malveillant sur l’ensemble du service pour aider à identifier les campagnes, puis permet aux administrateurs de les examiner de bout en bout, y compris les cibles, les impacts et les flux, qui sont également disponibles dans une écriture de campagne téléchargeable.

6. **Les compléments Message** de rapport permettent aux utilisateurs de signaler facilement les faux positifs (bon e-mail, marqués par erreur comme *mauvais*) ou les faux négatifs (e-mail incorrect marqué comme *bon*) à Microsoft pour une analyse plus approfondie.

7. **Les liens sécurisés pour les clients Office** offrent la même protection de temps de clic des liens sécurisés, en mode natif, à l’intérieur des applications Office prises en charge comme Word, PowerPoint et Excel.

8. **La protection pour OneDrive, SharePoint et Teams** offre la même protection des pièces jointes sécurisées contre les fichiers malveillants, en mode natif, à l’intérieur de OneDrive, SharePoint et Microsoft Teams.

9. Lorsqu’une URL qui pointe vers un fichier est sélectionnée après la remise, la **détonation de contenu lié** affiche une page d’avertissement jusqu’à ce que le bac à sable du fichier soit terminé et que l’URL soit jugée sécurisée.

## <a name="the-filtering-stack-diagram"></a>Diagramme de la pile de filtrage

Le diagramme final (comme avec toutes les parties du diagramme qui le compose) *est susceptible de changer à mesure que le produit grandit et se développe*. Créez un signet sur cette page et utilisez l’option **de commentaires** que vous trouverez en bas si vous devez demander après les mises à jour. Pour vos enregistrements, il s’agit de la pile avec toutes les phases dans l’ordre :

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png" alt-text="Toutes les phases de filtrage dans Defender pour Office 365 dans l’ordre, de 1 à 4" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png":::

## <a name="more-information"></a>Plus d’informations

Avez-vous besoin de configurer Microsoft Defender pour Office 365 ***right now** _? Utilisez cette pile, _now*, avec [cette étape pour](protect-against-threats.md) commencer à protéger votre organisation.

*Merci spécial de MSFTTracyP et de l’équipe d’écriture de documents à Giulian Garruba pour ce contenu*.
