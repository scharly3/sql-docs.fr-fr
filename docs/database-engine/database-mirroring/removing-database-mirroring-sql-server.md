---
title: "Suppression d&#39;une mise en miroir des bases de donn&#233;es (SQL Server) | Microsoft Docs"
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
  - "mise en miroir de bases de données [SQL Server], suppression"
  - "arrête de la mise en miroir de bases de données [SQL Server]"
  - "suppression de mise en miroir de bases de données [SQL Server]"
ms.assetid: 40c72091-8f03-4037-8b55-5e95309fe145
caps.latest.revision: 32
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 31
---
# Suppression d&#39;une mise en miroir des bases de donn&#233;es (SQL Server)
  Le propriétaire de la base de données peut arrêter manuellement une session de mise en miroir de base de données à tout moment et sur n'importe quel serveur partenaire.  
  
## Impact de la suppression d'une mise en mémoire  
 Lorsqu'une mise en miroir est supprimée, les événements suivants se produisent :  
  
-   Les relations qui existaient éventuellement entre les serveurs partenaires d'une part et entre chaque serveur partenaire et le serveur témoin d'autre part sont rompues définitivement.  
  
     Si les serveurs partenaires communiquaient entre eux lorsque la session a été arrêtée, leur relation est immédiatement rompue sur les deux ordinateurs. Si les serveurs partenaires ne communiquaient pas (la base de données présentait alors l'état DISCONNECTED au moment de l'arrêt), la relation est rompue immédiatement sur le serveur partenaire à partir duquel la mise en miroir a été arrêtée ; lorsque l'autre serveur partenaire essaie de se reconnecter, il découvre que la session de mise en miroir est terminée.  
  
-   Les informations sur la session de mise en miroir sont supprimées, ce qui n'est pas le cas lorsqu'une session est suspendue. La mise en miroir est supprimée de la base de données principale et de la base de données miroir. Dans **sys.databases**, la colonne **mirroring_state** et toutes les autres colonnes de mise en miroir indiquent la valeur NULL. Pour plus d’informations, consultez [sys.database_mirroring &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md).  
  
-   L'instance de chaque serveur partenaire conserve une copie distincte de la base de données.  
  
-   La base de données miroir conserve l’état RESTORING (consultez la colonne **state** de **sys.databases**), car elle a été créée par le biais de RESTORE WITH NORECOVERY. À ce stade, vous pouvez soit supprimer l'ancienne base de données miroir, soit la restaurer avec WITH RECOVERY. Après avoir récupéré la base de données, vous constatez qu'elle est différente de l'ancienne base de données principale. Cela s'explique par le fait que l'opération de récupération débute un nouveau branchement de récupération.  
  
> [!NOTE]  
>  Pour continuer la mise en miroir après l'arrêt d'une session, vous devez établir une nouvelle session de mise en miroir de base de données. Si vous créez une sauvegarde de fichier journal après l'arrêt de la mise en miroir, vous devez l'appliquer à la base de données miroir avant de redémarrer la mise en miroir.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour supprimer une mise en miroir de bases de données**  
  
-   [Supprimer une mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-database-mirroring-sql-server.md)  
  
 **Pour démarrer la mise en miroir de bases de données**  
  
-   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish database mirroring session - windows authentication.md)  
  
-   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [&#91;Haut&#93;](#Top)  
  
## Voir aussi  
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Suspendre et reprendre la mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/pausing-and-resuming-database-mirroring-sql-server.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  