---
title: "Classe d&#39;&#233;v&#233;nements Database Mirroring State Change | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "notifications d’événements [SQL Server], mise en miroir de bases de données"
  - "mise en miroir de bases de données [SQL Server], notifications d’événements"
  - "Database Mirroring State Change (classe d'événements)"
ms.assetid: f936a99e-2a81-4768-8177-5c969bbe2e04
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Classe d&#39;&#233;v&#233;nements Database Mirroring State Change
  La classe d’événements **Database Mirroring State Change** indique que l’état d’une base de données mise en miroir change. Incluez cette classe d'événements au sein des traces qui surveillent les conditions d'exécution des bases de données mises en miroir.  
  
 Lorsque la classe d’événements **Database Mirroring State Change** est incluse au sein d’une trace, la surcharge relative est peu élevée. La surcharge peut être plus importante si l'état des bases de données mises en miroir augmente.  
  
## Colonnes de données de la classe d'événements Data Database Mirroring State Change  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**Int**|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|**nvarchar**|Nom de la base de données mise en miroir.|35|Oui|  
|**EventClass**|**int**|Type d’événement = 167|27|Non|  
|**EventSequence**|**int**|Séquence de la classe d'événements dans le lot.|51|Non|  
|**IntegerData**|**int**|ID de l'état antérieur.|25|Oui|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous trouverez ces informations dans la vue de catalogue **sys.server_principals**. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**RequestID**|**int**|ID de la demande contenant l'instruction.|49|Oui|  
|**ServerName**|**nvarchar**|Nom de l’instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est tracée.|26|Non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**État**|**int**|ID du nouvel état de la mise en miroir :<br /><br /> 0 = Notification Null<br /><br /> 1 = Principal synchronisé avec témoin<br /><br /> 2 = Principal synchronisé sans témoin<br /><br /> 3 = Miroir synchronisé avec témoin<br /><br /> 4 = Miroir synchronisé sans témoin<br /><br /> 5 = Connexion avec principal perdue<br /><br /> 6 = Connexion avec miroir perdue<br /><br /> 7 =Basculement manuel<br /><br /> 8 = Basculement automatique<br /><br /> 9 = Mise en miroir suspendue<br /><br /> 10 = Pas de quorum<br /><br /> 11 = Synchronisation miroir<br /><br /> 12 = Principal en cours d'exécution exposé|30|Oui|  
|**TextData**|**ntext**|Description du changement d'état.|1|Oui|  
|**TransactionID**|**bigint**|ID affecté par le système à la transaction.|4|Oui|  
  
## Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  