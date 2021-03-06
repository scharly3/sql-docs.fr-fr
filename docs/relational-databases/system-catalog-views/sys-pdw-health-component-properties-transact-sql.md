---
title: Sys.pdw_health_component_properties (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 628432368c30d81f8a89b97baf1534ce9502403b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="syspdwhealthcomponentproperties-transact-sql"></a>Sys.pdw_health_component_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Stocke des propriétés qui décrivent un appareil. Certaines propriétés affichent l’état du périphérique et certaines propriétés décrivent l’appareil lui-même.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Identificateur unique de la propriété d’un composant.<br /><br /> property_id et id_composant forment la clé pour cette vue.|NOT NULL|  
|id_composant|**int**|L’ID du composant. Consultez [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id et id_composant forment la clé pour cette vue.|NOT NULL|  
|property_name|**nvarchar(255)**|Nom de la propriété.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nom de la propriété comme défini par le fabricant.|NOT NULL|  
|is_key|**bit**|Détermine si l’instance de périphérique est unique ou non.|NOT NULL<br /><br /> 0 - l’instance de périphérique est unique.<br /><br /> 1 - instance de l’appareil n’est pas unique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
