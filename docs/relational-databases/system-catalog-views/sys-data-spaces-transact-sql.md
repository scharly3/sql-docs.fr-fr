---
title: Sys.data_spaces (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- data_spaces
- sys.data_spaces_TSQL
- sys.data_spaces
- data_spaces_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.data_spaces catalog view
ms.assetid: f39d55fe-2c0f-472d-a77f-cebc6fea95b5
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f17714f7c16d120891873692769d0d2f764c2626
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysdataspaces-transact-sql"></a>sys.data_spaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour espace de données. Il peut s'agir d'un groupe de fichiers, d'un schéma de partition ou d'un groupe de fichiers de données FILESTREAM.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Nom de l'espace de données, unique dans la base de données.|  
|data_space_id|**int**|Numéro d'identification de l'espace de données, unique dans la base de données.|  
|Type|**char(2)**|Type de l'espace de données :<br /><br /> FG = groupe de fichiers<br /><br /> FD = groupe de fichiers de données FILESTREAM<br /><br /> FX = Groupe de fichiers de tables optimisée en mémoire<br /><br /> **S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> PS = schéma de partition|  
|type_desc|**nvarchar (60)**|Description du type de l'espace de données :<br /><br /> FILESTREAM_DATA_FILEGROUP<br /><br /> MEMORY_OPTIMIZED_DATA_FILEGROUP<br /><br /> **S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> PARTITION_SCHEME<br /><br /> ROWS_FILEGROUP|  
|is_default|**bit**|1 = Espace de données par défaut. Espace de données par défaut utilisé lorsqu'un groupe de fichiers ou un schéma de partition n'est pas spécifié dans une instruction CREATE TABLE ou CREATE INDEX.<br /><br /> 0 = N'est pas l'espace de données par défaut.|  
|is_system|**bit**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = L'espace de données est utilisé pour les fragments d'index de recherche en texte intégral.<br /><br /> 0 = L'espace de données n'est pas utilisé pour les fragments d'index de recherche en texte intégral.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle public. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Espaces de données &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [Sys.destination_data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [Sys.FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Sys.partition_schemes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [Interrogation des catalogues système SQL Server FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  