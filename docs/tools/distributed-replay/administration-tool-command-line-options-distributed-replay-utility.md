---
title: "Options de ligne de commande de l&#39;outil d&#39;administration (Distributed Replay Utility) | Microsoft Docs"
ms.custom: ""
ms.date: "08/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
caps.latest.revision: 35
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# Options de ligne de commande de l&#39;outil d&#39;administration (Distributed Replay Utility)
  L’outil d’administration [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay (**DReplay.exe**) est un outil de ligne de commande permettant de communiquer avec Distributed Replay Controller. Utilisez l’outil d’administration pour initier, surveiller et annuler des opérations sur le contrôleur.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.png "Icône Lien de rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées par l’outil d’administration, consultez [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## Syntaxe  
  
```  
  
dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-m controller] -i input_trace_file  
    -d controller_working_dir [-c config_file] [-f status_interval]  
  
  dreplay replay [-m controller] -d controller_working_dir [-o]  
    [-s target_server] -w clients [-c config_file]  
    [-f status_interval]  
  
  dreplay status [-m controller] [-f status_interval]  
  
  dreplay cancel [-m controller] [-q]   
```  
  
## Notes  
 Vous pouvez émettre les options de ligne de commande suivantes avec **DReplay.exe** :  
  
 **prétraitement**  
 Initialise l'étape de prétraitement. Le contrôleur prépare les données de trace d'entrée, que vous avez capturées dans l'environnement de production, pour la relecture sur le serveur cible.  
  
 **relecture**  
 Initialise l'étape de relecture d'événement. Le contrôleur distribue des données de relecture aux clients spécifiés, lance la relecture distribuée et synchronise les clients. Éventuellement, chaque client sélectionné enregistre l'activité de relecture et enregistre des fichiers de trace de résultats localement.  
  
 **status**  
 Interroge le contrôleur et affiche l'état en cours.  
  
 **annuler**  
 Annule l'opération actuelle qui s'exécute sur le contrôleur.  
  
 Pour obtenir des informations détaillées sur la syntaxe contenant les arguments de commande et des exemples, consultez les rubriques suivantes :  
  
-   [Option preprocess &#40;outil d’administration Distributed Replay&#41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)  
  
-   [Option replay &#40;outil d’administration Distributed Replay&#41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)  
  
-   [Option status &#40;outil d’administration Distributed Replay&#41;](../../tools/distributed-replay/status-option-distributed-replay-administration-tool.md)  
  
-   [Option cancel &#40;outil d’administration Distributed Replay&#41;](../../tools/distributed-replay/cancel-option-distributed-replay-administration-tool.md)  
  
 Les appels de procédure distante (RPC) sont rediffusés en tant que RPC et non comme événements de langage.  
  
## Autorisations  
 Vous devez exécuter l'outil d'administration en tant qu'utilisateur interactif, comme un utilisateur local ou un compte d'utilisateur de domaine. Pour utiliser un compte d'utilisateur local, l'outil d'administration et le contrôleur doivent s'exécuter sur le même ordinateur.  
  
 Pour plus d’informations, voir [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## Voir aussi  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  