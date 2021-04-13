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
localization_priority: Normal
description: Suivez le chemin d’accès d’un message entrant via la pile de filtrage des menaces dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0760bd7a67f175e4af114324ccc729355ad5f593
ms.sourcegitcommit: 4e05f19c00e172b65f637f19ca461db5b21dff4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51601375"
---
# <a name="step-by-step-threat-protection-in-microsoft-defender-for-office-365"></a>Protection pas à pas contre les menaces dans Microsoft Defender pour Office 365

La pile de protection ou de filtrage Microsoft Defender pour Office 365 peut être décomposée en 4 phases, comme dans cet article. En règle générale, le courrier entrant passe par toutes ces phases avant la remise, mais le chemin d’accès réel pris par le courrier électronique est soumis à la configuration de Defender pour Office 365 d’une organisation.

> [!TIP]
> Restez à l’écoute jusqu’à la fin de cet article pour obtenir un graphique unifié des 4 phases de Defender pour la protection Office 365 ! 

## <a name="phase-1---edge-protection"></a>Phase 1 - Edge Protection

Malheureusement, les blocs Edge qui étaient une *fois* critiques sont maintenant relativement simples à surmonter pour les mauvais acteurs. Au fil du temps, moins de trafic est bloqué ici, mais il reste une partie importante de la pile.  

Les blocs Edge sont conçus pour être automatiques. Dans le cas d’un faux positif, les expéditeurs sont avertis et leur dire comment résoudre leur problème. Les connecteurs de partenaires de confiance avec une réputation limitée peuvent garantir la livrabilité ou des substitutions temporaires peuvent être mises en place lors de l’intégration de nouveaux points de terminaison.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png" alt-text="La phase 1 du filtrage dans Defender pour Office 365 est la protection Edge.":::

1. **La limitation du** réseau protège l’infrastructure Office 365 et les clients contre les attaques par déni de service (DOS) en limitant le nombre de messages qui peuvent être envoyés par un ensemble spécifique d’infrastructure.

2. **La réputation et la limitation d’IP** bloquent l’envoi de messages provenant d’adresses IP de connexion connues et non bonnes. Si une adresse IP spécifique envoie de nombreux messages sur une courte période, ils seront limitées.

3. **La réputation du** domaine bloque l’envoi de messages provenant d’un domaine connu comme étant mauvais.

4. **Le filtrage Edge basé sur l’annuaire** bloque les tentatives de recherche des informations d’annuaire d’une organisation via SMTP.

5. **La détection de la backscatter** empêche une organisation d’être attaquer par le biais de rapports de non-remise non valides.

6. **Le filtrage amélioré pour les connecteurs conserve** les informations d’authentification même lorsque le trafic passe par un autre appareil avant d’atteindre Office 365. Cela améliore la précision de la pile de filtrage, y compris le clustering heuristique, la protection contre l’usurpation d’informations et les modèles d’apprentissage automatique anti-hameçonnage, même dans des scénarios de routage complexes ou hybrides.

## <a name="phase-2---sender-intelligence"></a>Phase 2 : Intelligence des expéditeurs

Les fonctionnalités d’intelligence de l’expéditeur sont essentielles pour détecter le courrier indésirable, le courrier indésirable, l’emprunt d’identité et les messages usurpés non autorisés, et également prendre en compte la détection du hameçonnage. La plupart de ces fonctionnalités sont configurables individuellement.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png" alt-text="La phase 2 du filtrage dans MDO est l’intelligence de l’expéditeur.":::

1. **Les déclencheurs et** alertes de détection de compromission de compte sont déclenchés lorsqu’un compte présente un comportement anormal, cohérent avec la compromission. Dans certains cas, le compte d’utilisateur est bloqué et empêché d’envoyer d’autres messages électroniques jusqu’à ce que le problème soit résolu par l’équipe des opérations de sécurité d’une organisation.

2. **L’authentification** de messagerie implique des méthodes configurées par le client et des méthodes configurées dans le cloud, visant à s’assurer que les expéditeurs sont autorisés et authentifiés. Ces méthodes résistant à l’usurpation d’usurpation.
    - **SPF peut** rejeter des messages basés sur des enregistrements TXT DNS répxant les adresses IP et les serveurs autorisés à envoyer des messages au nom de l’organisation.
    - **DKIM** fournit une signature chiffrée qui authentifier l’expéditeur.
    - **DMARC permet** aux administrateurs de marquer SPF et DKIM comme requis dans leur domaine et applique l’alignement entre les résultats de ces deux technologies.
    - **ARC** n’est pas configuré par le client, mais s’appuie sur DMARC pour travailler avec le forwarding dans les listes de publipostage, lors de l’enregistrement d’une chaîne d’authentification.

3.  La veille contre l’usurpation d’adresse est capable de filtrer les personnes autorisées à « usurper » (c’est-à-dire, celles qui envoient des messages au nom d’un autre compte ou qui sont envoyées pour une liste de diffusion) à partir d’usurpateurs malveillants qui s’attaquent à un domaine d’organisation ou externe connu. Elle sépare les messages légitimes « de la part de » de l’usurpation d’expéditeurs pour remettre les messages de courrier indésirable et de hameçonnage. 

    **La veille contre l’usurpation d’informations intra-organisationnelle** détecte et bloque les tentatives d’usurpation d’informations à partir d’un domaine au sein de l’organisation.

4. **La veille contre** l’usurpation d’usurpation d’un domaine détecte et bloque les tentatives d’usurpation d’informations provenant d’un domaine extérieur à l’organisation.

5. **Le filtrage en bloc** permet aux administrateurs de configurer un niveau de confiance en bloc (BCL) indiquant si le message a été envoyé à partir d’un expéditeur en bloc. Les administrateurs peuvent utiliser le curseur en bloc dans la stratégie anti-courrier indésirable pour déterminer le niveau de courrier en nombre à traiter comme courrier indésirable.

6. **L’intelligence des boîtes** aux lettres apprend les comportements de messagerie standard de l’utilisateur. Il exploite le graphique de communication d’un utilisateur pour détecter quand un expéditeur semble être une personne avec qui l’utilisateur communique généralement, mais qui est en réalité malveillante. Cette méthode détecte l’emprunt d’identité.

7. **L’emprunt d’identité** d’intelligence de boîte aux lettres active ou désactive les résultats d’emprunt d’identité améliorés en fonction de la carte d’expéditeur individuelle de chaque utilisateur. Lorsqu’elle est activée, cette fonctionnalité permet d’identifier l’emprunt d’identité.

8. **L’emprunt d’identité** d’utilisateur permet à un administrateur de créer une liste de cibles à valeur élevée susceptibles d’être usurpées. Si un message arrive là où l’expéditeur semble avoir uniquement le même nom et la même adresse que le compte à valeur élevée protégé, le message est marqué ou marqué. (Par exemple, *trα cye@contoso.com* pour *tracye@contoso.com*).

9. **L’emprunt d’identité** de domaine détecte les domaines qui sont similaires au domaine du destinataire et qui tentent de ressembler à un domaine interne. Par exemple, cet emprunt *d’tracye@liw α re.com* pour *tracye@litware.com*.

## <a name="phase-3---content-filtering"></a>Phase 3 : Filtrage du contenu

Dans cette phase, la pile de filtrage commence à gérer le contenu spécifique du courrier, y compris ses liens hypertexte et ses pièces jointes.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png" alt-text="La phase 3 du filtrage dans MDO est le filtrage de contenu.":::

1. **Les règles de** transport (également appelées règles de flux de messagerie ou règles de transport Exchange) permettent à un administrateur d’prendre un large éventail d’actions lorsqu’un large éventail de conditions est respecté pour un message. Tous les messages qui circulent dans votre organisation sont évalués par rapport aux règles de flux de messagerie/règles de transport activées.

2. **L’Antivirus Microsoft Defender** et deux moteurs *antivirus* tiers sont utilisés pour détecter tous les programmes malveillants connus dans les pièces jointes.

3. Les moteurs antivirus sont également utilisés pour taper toutes les pièces  jointes de sorte que le blocage des types puisse bloquer toutes les pièces jointes de types spécifiés par l’administrateur.

4. Chaque fois que Microsoft Defender pour Office 365 détecte une pièce jointe malveillante, le hachage du fichier et un hachage de son contenu actif sont ajoutés à la réputation d’Exchange Online Protection (EOP). **Le blocage de la** réputation des pièces jointes bloque ce fichier sur tous les Office 365 et sur les points de terminaison, via les appels cloud MSAV.

5. **Le clustering heuristique** peut déterminer qu’un fichier est suspect en fonction de l’heuristique de remise. Lorsqu’une pièce jointe suspecte est trouvée, l’intégralité de la campagne est suspendue et le fichier est en bac à sable. Si le fichier est jugé malveillant, toute la campagne est bloquée.

6. **Les modèles d’apprentissage** automatique agissent sur l’en-tête, le contenu du corps et les URL d’un message pour détecter les tentatives de hameçonnage.

7. Microsoft utilise une détermination de la réputation à partir du bac à sable (sandbox) d’URL, ainsi que de la réputation d’URL provenant de flux tiers dans le blocage de la réputation de **l’URL,** pour bloquer tout message avec une URL malveillante connue.

8. **Les heuristiques de contenu** peuvent détecter des messages suspects en fonction de la structure et de la fréquence des mots dans le corps du message, à l’aide de modèles d’apprentissage automatique.

9. **Les pièces jointes sécurisées** bac à sable (sandbox) de chaque pièce jointe pour les clients Defender pour Office 365, à l’aide de l’analyse dynamique pour détecter les menaces jamais vues.

10. **La détonation de** contenu lié traite chaque URL liée à un fichier dans un e-mail comme une pièce jointe, en bac à sable (sandbox) asynchrone au moment de la remise.

11. **Le détonation d’URL** se produit lorsque la technologie anti-hameçonnage en amont trouve qu’un message ou une URL est suspect. La détonation d’URL bac à sable (sandbox) permet d’afficher les URL du message au moment de la remise.

## <a name="phase-4---post-delivery-protection"></a>Phase 4 : Protection après remise

La dernière étape a lieu après la remise du courrier ou du fichier, agissant sur le courrier qui se trouve dans différentes boîtes aux lettres, fichiers et liens qui apparaissent dans des clients tels que Microsoft Teams.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png" alt-text="La phase 4 du filtrage dans Defender pour Office 365 est la protection post-remise.":::

1. **La protection de** liens sécurisés est la protection au moment du clic de MDO. Chaque URL de chaque message est enveloppée pour pointer vers les serveurs de liens sécurisés Microsoft. Lorsqu’un utilisateur clique sur une URL, elle est vérifiée par rapport à la dernière réputation, avant que l’utilisateur soit redirigé vers le site cible. L’URL est en bac à sable asynchrone pour mettre à jour sa réputation.

2. **Le hameçonnage Zero-Hour la purge automatique (ZAP)** détecte et s’attaque aux messages de hameçonnage malveillants qui ont déjà été remis aux boîtes aux lettres Exchange Online.

3. **La protection ZAP contre** les programmes malveillants détecte et programme d’attaque les messages malveillants qui ont déjà été remis aux boîtes aux lettres Exchange Online.

4. **La loi ZAP de** courrier indésirable détecte et détecte de manière malveillante les messages de courrier indésirable qui ont déjà été remis aux boîtes aux lettres Exchange Online.

5. **Les affichages campagnes** offrent aux administrateurs une vue d’ensemble d’une attaque, plus rapidement et plus complètement que n’importe quelle équipe ne pourrait l’être sans automatisation. Microsoft exploite les grandes quantités de données anti-hameçonnage, anti-courrier indésirable et anti-programme malveillant dans l’ensemble du service pour identifier les campagnes, puis permet aux administrateurs de les examiner de bout en bout, y compris les cibles, les impacts et les flux, qui sont également disponibles dans une écriture de campagne téléchargeable.

6. **Les add-ins** Signaler un message permettent aux utilisateurs de signaler facilement à Microsoft des faux positifs (bon e-mail, marqués par erreur comme faux *)* ou des faux négatifs (courriers électroniques erronés marqués comme étant *bons)* à Microsoft pour une analyse plus approfondie.

7. **Les clients Liens sécurisés** pour Office offrent la même protection en temps de clic des liens sécurisés, en natif, à l’intérieur des clients Office tels que Word, PowerPoint et Excel.

8. **La protection pour OneDrive, SharePoint** et Teams offre la même protection contre les pièces jointes sécurisées contre les fichiers malveillants, en natif, à l’intérieur de OneDrive, SharePoint et Microsoft Teams.

9. Lorsqu’une URL qui pointe vers un fichier est sélectionnée après la remise, la **détonation** de contenu lié affiche une page d’avertissement jusqu’à ce que le bac à sable du fichier soit terminé et que l’URL soit sûre.


## <a name="the-filtering-stack-diagram"></a>Diagramme de pile de filtrage

Le diagramme final (comme pour toutes les parties du diagramme qui le compose) peut être changé à mesure que le produit croît *et se développe.* Signetz cette page  et utilisez l’option de commentaires que vous trouverez en bas si vous devez demander après les mises à jour. Pour vos enregistrements, il s’agit de la pile avec toutes les phases dans l’ordre :

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png" alt-text="Toutes les phases de filtrage dans MDO dans l’ordre, 1 à 4.":::

## <a name="more-information"></a>Plus d’informations

Avez-vous besoin de configurer Microsoft Defender pour Office 365 ***maintenant** _? Utilisez cette pile, _now*, avec cette étape par [étape](protect-against-threats.md) pour commencer à protéger votre organisation.

*Nous remercions tout particulièrement MSFTTracyP* et l’équipe d’écriture de documents pour ce contenu.