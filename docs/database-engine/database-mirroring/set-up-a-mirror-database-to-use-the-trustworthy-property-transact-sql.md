---
title: "Configurer une base de donn&#233;es miroir pour utiliser la propri&#233;t&#233; Trustworthy (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TRUSTWORTHY (option de base de données)"
  - "miroir de bases de données [SQL Server]"
  - "mise en miroir de bases de données (SQL Server), sécurité"
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# Configurer une base de donn&#233;es miroir pour utiliser la propri&#233;t&#233; Trustworthy (Transact-SQL)
  Lorsqu'une base de données est sauvegardée, la valeur OFF est attribuée à la propriété TRUSTWORTHY de la base de données. Par conséquent, la propriété TRUSTWORTHY d'une nouvelle base de données miroir a toujours la valeur OFF. Si la base de données doit être fiable après un basculement, des opérations de configuration supplémentaires sont requises après le début de la mise en miroir.  
  
> [!NOTE]  
>  Pour plus d’informations sur cette propriété de base de données, consultez [Propriété de base de données TRUSTWORTHY](../../relational-databases/security/trustworthy-database-property.md).  
  
## Procédure  
  
#### Pour configurer une base de données miroir pour qu'elle utilise la propriété Trustworthy  
  
1.  Sur l'instance du serveur principal, vérifiez que la propriété Trustworthy de la base de données principale est activée.  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     Pour plus d’informations, consultez [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
2.  Après avoir démarré la mise en miroir, vérifiez que la base de données est actuellement la base de données principale, que la session utilise un mode de fonctionnement synchrone et que la session est toujours synchronisée.  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     Pour plus d’informations, consultez [sys.database_mirroring &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md).  
  
3.  Une fois la session de mise en miroir synchronisée, basculez manuellement vers la base de données miroir.  
  
     Cette opération est possible dans SQL Server Management Studio ou en utilisant Transact-SQL :  
  
    -   [Basculer manuellement une session de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Basculer manuellement une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  Activez la propriété Trustworthy de la base de données en utilisant la commande ALTER DATABASE suivante :  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
5.  Vous pouvez également basculer manuellement de nouveau vers la base de données principale d'origine.  
  
6.  Vous pouvez également passer en mode hautes performances asynchrone en attribuant la valeur OFF à SAFETY et en garantissant que WITNESS a aussi la valeur OFF.  
  
     Dans Transact-SQL :  
  
    -   [Modifier la sécurité des transactions dans une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [Supprimer le témoin d’une session de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     Dans SQL Server Management Studio :  
  
    -   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish database mirroring session - windows authentication.md)  
  
## Voir aussi  
 [Propriété de base de données TRUSTWORTHY](../../relational-databases/security/trustworthy-database-property.md)   
 [Configurer une base de données miroir chiffrée](../../database-engine/database-mirroring/set-up-an-encrypted-mirror-database.md)  
  
  