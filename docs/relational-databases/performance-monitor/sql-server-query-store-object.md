---
title: "SQL Server, objet de magasin de requ&#234;tes | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Objet de magasin de requêtes"
  - "SQL Server:Query Store"
ms.assetid: b4a04acd-0b66-44a5-b72d-1a45b49e13e6
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# SQL Server, objet de magasin de requ&#234;tes
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  L’objet de magasin de requêtes fournit des compteurs pour surveiller l’utilisation des ressources de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de stocker les textes des requêtes, les plans d’exécution et les statistiques d’exécution concernant les objets tels que les procédures stockées, les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ad hoc et préparées, et les déclencheurs.  
  
 Ce tableau décrit les compteurs **SQLServer:Query Store**.  
  
|Compteurs de magasin de requêtes SQL Server|Description|  
|-------------------------------------|-----------------|  
|**Utilisation de l’UC du magasin de requêtes**|Indique l’utilisation de l’UC des magasins de requête.|  
|**Lectures logiques du magasin de requêtes**|Indique le nombre de lectures logiques effectuées par le magasin de requêtes.|  
|**Écritures logiques du magasin de requêtes**|Indique la quantité de données mise en file d’attente avant la vidange du magasin de requêtes. La fréquence et le délai d’ajout d’éléments (représentant les statistiques d’exécution) dans la file d’attente sont contrôlés par le paramètre Intervalle de vidange de données.|  
|**Lectures physiques du magasin de requêtes**|Indique le nombre de lectures physiques effectuées par le magasin de requêtes.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Instance de magasin de requêtes|Description|  
|--------------------------|-----------------|  
|**_Total**|Informations relatives au magasin de requêtes pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|\< nom de la base de données>|Informations relatives au magasin de requête pour cette base de données.|  
  
## Voir aussi  
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Query Store Stored Procedures &#40;Transact-SQL&#41; [Procédures stockées du magasin de requêtes &#40;Transact-SQL&#41;]](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [Query Store Catalog Views &#40;Transact-SQL&#41; [Affichages catalogue du magasin de requêtes &#40;Transact-SQL&#41;]](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  