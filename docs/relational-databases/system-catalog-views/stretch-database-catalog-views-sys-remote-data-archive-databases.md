---
title: Sys.remote_data_archive_databases (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_databases
- sys.remote_data_archive_databases_TSQL
- remote_data_archive_databases
- remote_data_archive_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_databases catalog view
ms.assetid: 25bffb0c-9821-40b4-88cf-75f854891a09
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b67f68c2208ab54cfa87a04db98d6e953a25ede0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="stretch-database-catalog-views---sysremotedataarchivedatabases"></a>Étendre des affichages catalogue de base de données - sys.remote_data_archive_databases
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque base de données distante qui stocke les données à partir d’une base de données locale prenant en charge Stretch.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|L’identificateur local généré automatiquement de la base de données distante.|  
|**remote_database_name**|**sysname**|Le nom de la base de données distante.|  
|**data_source_id**|**int**|La source de données utilisée pour se connecter au serveur distant|  
  
## <a name="see-also"></a>Voir aussi  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
