---
title: "Pr&#233;sentation de l&#39;interface du moniteur de r&#233;plication | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Moniteur de réplication"
  - "moniteur de réplication, à propos du moniteur de réplication"
ms.assetid: 078f0e34-7153-45c4-8725-778b5bef88da
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Pr&#233;sentation de l&#39;interface du moniteur de r&#233;plication
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Moniteur de réplication présente une vue, axée sur le serveur de publication ou la vue, axée sur le serveur de distribution de toutes les activités de réplication dans un format à deux volets. Vous ajoutez un serveur de publication au moniteur dans le volet gauche tandis que dans le volet droit, le moniteur affiche des informations sur le serveur de publication, ses publications, les abonnements à ces publications ainsi que les divers agents de réplication. Outre la présentation des informations pour la topologie de réplication, le moniteur de réplication vous permet d'effectuer diverses tâches, telles que le démarrage et l'arrêt d'agents, ainsi que la validation des données.  
  
## Affichage d'informations relatives à la topologie complète  
 Le volet gauche du Moniteur de réplication affiche  
  
-   Les groupes de serveurs de publication, les serveurs de publication et les publications.  
  
-   Les serveurs de distribution, les serveurs de publication et les publications.  
  
 Pour afficher des informations dans le moniteur de réplication, vous devez d'abord ajouter un serveur de publication. Pour plus d’informations, consultez [Ajouter et supprimer les éditeurs à partir du moniteur de réplication](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md).  
  
 Le volet gauche vous aide à répondre aux questions suivantes :  
  
-   L'intégrité de mon système de réplication est-elle de bonne qualité ?  
  
     L'intégrité du système de réplication est relativement correcte si aucune icône d'erreur n'apparaît en regard des nœuds dans le volet gauche. Pour obtenir une vue complète de l’intégrité du système, vous devez également vérifier le **liste de suivi** onglet, qui affiche des informations sur les abonnements qui peuvent nécessiter une attention particulière.  
  
-   Pourquoi un Agent de fonctionne pas ?  
  
     Un agent ne s'exécute pas à un moment donné soit parce qu'il n'est pas programmé pour le faire, soit parce qu'une erreur s'est produite. Si une erreur s'est produite, une icône d'erreur s'affiche en regard des nœuds appropriés dans le volet gauche. Par exemple, si l'Agent d'instantané d'une publication s'est arrêté du fait d'une erreur, une icône d'erreur s'affiche en regard du nœud Groupe du serveur de publication, Publication et des nœuds de publication. Informations de résumé pour l’Agent de capture instantanée s’affiche sur la **Agents** pour la publication de l’onglet, double-cliquez sur l’Agent de capture instantanée de cet onglet pour des informations détaillées.  
  
## Affichage d'informations et réalisation de tâches associées aux serveurs de distribution  
 Le moniteur de réplication présente des informations sur les serveurs de distribution dans trois onglets :  
  
-   **Publications** onglet  
  
     Cet onglet fournit des informations de résumé pour toutes les publications d'un serveur de distribution.  
  
-   **Liste de suivi** onglet  
  
     Cet onglet fournit des informations sur les abonnements pour le serveur de distribution sélectionné. Vous pouvez filtrer la liste des abonnements pour identifier les erreurs, les avertissements et les abonnements qui ne fonctionnent pas correctement. Cet onglet vous permet également d'effectuer les tâches suivantes : accéder aux propriétés d'abonnement, accéder aux informations détaillées sur l'agent ou les agents associés à un abonnement, réinitialiser des abonnements et valider des abonnements.  
  
     Le **liste de suivi** onglet vous aide à répondre aux questions suivantes :  
  
    -   Quels sont les abonnements lents ?  
  
         Définissez des options dans cet onglet pour que les abonnements soient présentés dans la grille dans l'ordre de leurs performances.  
  
    -   L'intégrité de mon système de réplication est-elle de bonne qualité ?  
  
         La grille de cet onglet présente des icônes d'erreur et d'avertissement pour tous les abonnements qui nécessitent une attention particulière.  
  
     Cet onglet n’est pas disponible pour les distributeurs qui exécutent des versions de [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] ou une version antérieure.  
  
-   **Agents** onglet  
  
     Cet onglet affiche les informations détaillées sur les agents et les travaux utilisés par tous les types de réplication. L'onglet permet également de démarrer et d'arrêter chaque agent ou travail.  
  
 Le moniteur de réplication fournit également un menu contextuel pour le nœud Serveur de distribution. Cliquez avec le bouton droit sur un serveur de distribution dans le volet gauche pour effectuer les tâches suivantes :  
  
-   Ajouter un serveur de publication au moniteur de réplication.  
  
-   Modifier les paramètres du moniteur de réplication pour le serveur de publication.  
  
-   Basculer dans la vue Groupe de serveurs de publication.  
  
## Affichage d'informations et réalisation de tâches associées aux serveurs de publication  
 Le moniteur de réplication présente des informations sur les serveurs de publication dans trois onglets :  
  
-   **Publications** onglet  
  
     Cet onglet fournit des informations de résumé pour toutes les publications sur un serveur de publication.  
  
-   **Liste de suivi** onglet  
  
     Cet onglet affiche des informations sur les abonnements provenant de toutes les publications disponibles sur le serveur de publication sélectionné. Vous pouvez filtrer la liste des abonnements pour identifier les erreurs, les avertissements et les abonnements qui ne fonctionnent pas correctement. Cet onglet vous permet également de : accéder aux propriétés d'abonnement, accéder aux informations détaillées sur l'agent ou les agents associés à un abonnement, réinitialiser des abonnements et valider des abonnements.  
  
     Le **liste de suivi** onglet vous aide à répondre aux questions suivantes :  
  
    -   Quels sont les abonnements lents ?  
  
         Définissez des options dans cet onglet pour que les abonnements soient présentés dans la grille dans l'ordre de leurs performances.  
  
    -   L'intégrité de mon système de réplication est-elle de bonne qualité ?  
  
         La grille de cet onglet présente des icônes d'erreur et d'avertissement pour tous les abonnements qui nécessitent une attention particulière.  
  
     Cet onglet ne s'affiche pas pour les serveurs de distribution exécutant des versions antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   **Agents** onglet  
  
     Cet onglet affiche les informations détaillées sur les agents et les travaux utilisés par tous les types de réplication. L'onglet permet également de démarrer et d'arrêter chaque agent ou travail.  
  
 Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour un serveur de publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md).  
  
 Le moniteur de réplication fournit également un menu contextuel pour le nœud Serveur de publication. Cliquez avec le bouton droit sur un serveur de publication dans le volet gauche pour effectuer les tâches suivantes :  
  
-   modifier les paramètres du moniteur de réplication pour le serveur de publication ;  
  
-   supprimer le serveur de publication du moniteur de réplication ;  
  
-   afficher et modifier des profils d'agents ;  
  
-   vous connecter ou vous déconnecter du serveur de distribution qui stocke des informations sur le serveur de publication.  
  
## Affichage d'informations et réalisation de tâches associées aux publications  
 Le moniteur de réplication présente des informations sur les publications dans trois onglets ainsi que dans plusieurs fenêtres de détails :  
  
-   **Tous les abonnements** onglet  
  
     Cet onglet montre des informations sur tous les abonnements à la publication sélectionnée. Par défaut, cet onglet est trié par ordre de priorité : erreurs, puis avertissements, ensuite dans l'ordre croissant des performances (les abonnements les moins performants étant tout en haut).  
  
     Le **tous les abonnements** onglet vous aide à répondre aux questions suivantes :  
  
    -   Quels sont les abonnements lents ?  
  
         Définissez des options dans cet onglet pour que les abonnements soient présentés dans la grille dans l'ordre de leurs performances.  
  
    -   L'intégrité de mon système de réplication est-elle de bonne qualité ?  
  
         La grille de cet onglet présente des icônes d'erreur et d'avertissement pour tous les abonnements qui nécessitent une attention particulière.  
  
-   **Agents** onglet  
  
     Cet onglet affiche des informations sur les agents utilisés par la réplication. Cet onglet affiche des informations sur les agents suivants :  
  
    -   Agent d'instantané, utilisé par toutes les publications  
  
    -   Agent de lecture du journal, utilisé par toutes les publications transactionnelles  
  
    -   Agent de lecture de la file d'attente, utilisé par les publications transactionnelles qui possèdent des abonnements mis à jour en attente  
  
     L'onglet permet aussi d'effectuer les tâches suivantes : accéder aux informations détaillées à propos de chaque agent, et démarrer ou arrêter chaque agent. Pour plus d'informations sur les agents associés aux abonnements (l'Agent de distribution et l'Agent de fusion), consultez la section « Affichage d'informations et réalisation de tâches associées aux abonnements » dans cette rubrique.  
  
-   **Avertissements** onglet  
  
     Cet onglet permet de spécifier des avertissements et des alertes pour les agents. Pour plus d’informations, consultez [définition des seuils et des avertissements dans le moniteur de réplication](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
-   **Les jetons de suivi** onglet (réplication transactionnelle uniquement)  
  
     Cet onglet permet de mesurer la latence, à savoir le temps écoulé entre la validation d'une transaction sur le serveur de publication et la validation de la transaction correspondante sur l'Abonné.  
  
     Cet onglet vous aide à répondre à la question suivante :  
  
    -   Combien de temps mettra une transaction validée maintenant pour atteindre un Abonné avec la réplication transactionnelle ?  
  
         Affichez le temps total que met une transaction pour se déplacer dans le système et comparez-le aux temps précédents.  
  
     Cet onglet ne s'affiche pas pour les serveurs de distribution exécutant [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] ou des versions antérieures. Pour plus d’informations sur les jetons de suivi, consultez [mesure la latence et valider les connexions pour la réplication transactionnelle](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
-   les fenêtres de détails concernant les agents associés à une publication. Les agents suivants sont associés aux publications :  
  
    -   Agent d'instantané, utilisé par toutes les publications  
  
    -   Agent de lecture du journal, utilisé par toutes les publications transactionnelles  
  
    -   Agent de lecture de la file d'attente, utilisé par les publications transactionnelles qui possèdent des abonnements mis à jour en attente  
  
     Dans le moniteur de réplication, double-cliquez sur un agent pour accéder aux informations dans une fenêtre de détails. En plus des agents répertoriés ci-dessus, il existe des agents associés aux abonnements : l'agent de distribution pour les abonnements à l'instantané et aux publications transactionnelles et l'agent de fusion pour les abonnements à des publications de fusion. Pour plus d'informations, consultez la section « Affichage d'informations et réalisation de tâches associées aux abonnements » dans cette rubrique.  
  
     Les fenêtres de détails des agents fournissent des informations sur les sessions des agents, notamment l'heure de début, l'heure de fin, la durée et les opérations effectuées dans une session. Elles vous aident à répondre à la question suivante :  
  
    -   Pourquoi un Agent de fonctionne pas ?  
  
         Les messages d'erreur disponibles fournissent des informations détaillées sur la raison de la non-exécution d'un agent et constituent un point de départ à la résolution des problèmes liés aux agents associés à une publication.  
  
 Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md) et [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
 Le moniteur de réplication fournit également un menu contextuel pour le nœud de publications. Cliquez avec le bouton droit sur un serveur de publication dans le volet gauche pour effectuer les opérations suivantes :  
  
-   réinitialiser tous les abonnements à une publication ;  
  
-   valider tous les abonnements à une publication ;  
  
-   générer un instantané pour une publication ;  
  
-   afficher et modifier les propriétés d'une publication.  
  
## Affichage d'informations et réalisation de tâches associées aux abonnements  
 Le moniteur de réplication présente des informations sur les abonnements dans plusieurs onglets. Dans le moniteur de réplication, double-cliquez sur un abonnement pour accéder à ces onglets dans une fenêtre de détails. Tous les onglets sont utiles pour répondre à la question « Pourquoi un agent ne s'exécute-t-il pas ? » Les messages d'erreur disponibles fournissent des informations détaillées sur la raison de la non-exécution d'un agent et constituent un point de départ à la résolution des problèmes liés aux agents associés à un abonnement.  
  
-   **Onglet Abonnements toutes** et **onglet liste de suivi.**  
  
     Ces onglets sont décrits plus haut dans cette rubrique.  
  
-   **Serveur de publication dans l’historique du serveur de distribution** onglet (réplication transactionnelle uniquement)  
  
     Cet onglet présente des informations sur l'Agent de lecture du journal pour une publication (identique à la fenêtre de détails de l'Agent de lecture du journal).  
  
-   **Serveur de distribution vers l’abonné historique** onglet (réplication de capture instantanée et la réplication transactionnelle)  
  
     Cet onglet présente des informations sur l'Agent de distribution pour un abonnement.  
  
-   **Commandes non distribuées** onglet (réplication transactionnelle uniquement)  
  
     Cet onglet présente des informations sur le nombre de commandes de la base de données de distribution qui n'ont pas été remises à l'Abonné sélectionné, ainsi que le temps estimé de remise de ces commandes. Cet onglet vous aide à répondre à la question « Quel est le retard de mon abonnement ? » Cet onglet ne s'affiche pas pour les serveurs de distribution exécutant des versions antérieures à SQL Server 2005.  
  
-   **Historique de synchronisation** onglet (réplication de fusion uniquement)  
  
     Cet onglet présente des informations sur l'Agent de fusion pour un abonnement. Il vous aide à répondre à la question suivante :  
  
    -   Pourquoi mon abonnement de fusion est-il lent ?  
  
         Cet onglet fournit des statistiques détaillées sur chaque article traité pendant la synchronisation, notamment la durée de chaque phase de traitement (téléchargement des modifications amont/aval, etc.). Il permet d'identifier les tables qui provoquent des ralentissements et il est l'emplacement idéal pour résoudre les problèmes de performances posés par les abonnements de fusion.  
  
 Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md) et [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Affichage d'informations et réalisation de tâches associées aux profils d'agents  
 Le moniteur de réplication inclut plusieurs boîtes de dialogue permettant de gérer les profils d'agents. Les profils d'agents sont des ensembles de paramètres qui déterminent le comportement des agents. Pour plus d’informations, voir [Replication Agent Profiles](../../../relational-databases/replication/agents/replication-agent-profiles.md). Les boîtes de dialogue sont les suivantes :  
  
-   **Profils de l'Agent**  
  
     Cette boîte de dialogue vous permet de : modifier les propriétés des profils, créer et supprimer des profils, spécifier un profil par défaut et spécifier que tous les agents d'un type donné (tels les Agents d'instantané) doivent utiliser un profil donné.  
  
-   **\< AgentProfileName> Propriétés**  
  
     Cette boîte de dialogue vous permet d'afficher et de modifier les paramètres d'un profil.  
  
-   **Nouveau profil de l'Agent**  
  
     Cette boîte de dialogue vous permet de créer un profil incluant en option les valeurs d'un profil existant.  
  
## Voir aussi  
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  