---
title: Sys.pdw_table_distribution_properties (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b25340c2fc69754233f4faca320ccf5c83897fb7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="syspdwtabledistributionproperties-transact-sql"></a>Sys.pdw_table_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations de distribution pour les tables.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|ID de la table pour les trois propriétés ont été spécifiées.||  
|**distribution_policy**|**tinyint**|0 = NON DÉFINI<br /><br /> 1 = NONE<br /><br /> 2 = HASH<br /><br /> 3 = RÉPLIQUE<br /><br /> 4 = ROUND_ROBIN|REPLICATE s’applique uniquement aux [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|  
|**distribution_policy_desc**|**nvarchar(60)**|NON DÉFINI, NONE, LE HACHAGE, RÉPLIQUER, SEGMENTED_HEAP|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Retourne le hachage ou REPLICATE.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
