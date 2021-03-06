---
title: Création d’une table temporelle à mémoire optimisée avec version gérée par le système
ms.custom: ''
ms.date: 05/05/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c1fc682-bf5b-4096-a0ff-3235d71c205a
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b742111490567ee1a10ce22fbd8c2c6592d10361
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="creating-a-memory-optimized-system-versioned-temporal-table"></a>Création d’une table temporelle à mémoire optimisée avec version gérée par le système
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  De même qu’il est possible de créer une table de l’historique sur disque, vous pouvez créer une table temporelle à mémoire optimisée et ce, de différentes manières.  
  
> [!NOTE]  
>  Pour créer des tables optimisées en mémoire, vous devez d’abord créer le [Groupe de fichiers mémoire optimisé](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md).  
  
 La création d’une table temporelle avec une table de l’historique par défaut est une option pratique lorsque vous voulez contrôler l’affectation des noms. Elle dépend toujours du système pour créer la table de l’historique avec la configuration par défaut. Dans l’exemple ci-dessous, une nouvelle table temporelle de contrôle de version du système à mémoire optimisée est liée à une nouvelle table de l’historique basée sur des disques.  
  
```  
CREATE SCHEMA History  
GO  
CREATE TABLE dbo.Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY NONCLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH   
    (  
        MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA,  
            SYSTEM_VERSIONING = ON ( HISTORY_TABLE = History.DepartmentHistory )   
    );  
```  
  
 Il est utile de créer une table temporelle liée à une table de l’historique existante lorsque vous devez activer le contrôle de version du système à l’aide d’une table existante, par exemple quand vous voulez migrer une solution temporelle personnalisée vers une prise en charge intégrée. Dans l’exemple ci-dessous, une table temporelle est créée et liée à une table de l’historique existante.  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY NONCLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (  
        SYSTEM_VERSIONING = ON  
            (  
                HISTORY_TABLE = dbo.Department_History  
                , DATA_CONSISTENCY_CHECK = ON   
            )  
        , MEMORY_OPTIMIZED = ON  
        , DURABILITY = SCHEMA_AND_DATA  
    );  
```  
 
## <a name="see-also"></a> Voir aussi  
 [Tables temporelles avec version gérée par le système avec tables à mémoire optimisée](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Utilisation des tables temporelles avec contrôle de version du système à mémoire optimisée](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)   
 [Surveillance des tables temporelles avec contrôle de version du système à mémoire optimisée](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)   
 [Considérations relatives aux performances des tables temporelles optimisées en mémoire à version contrôlée par le système](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)   
 [Tables temporelles](../../relational-databases/tables/temporal-tables.md)   
 [Vérifications de cohérence système des tables temporelles](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Gérer la rétention des données d’historique dans les tables temporelles avec version gérée par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Vues et fonctions de métadonnées de table temporelle](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
