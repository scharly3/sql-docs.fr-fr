---
title: Sys.fn_hadr_distributed_ag_replica (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_distributed_ag_replica
- sys.fn_hadr_distributed_ag_replica_TSQL
- fn_hadr_distributed_ag_replica
- fn_hadr_distributed_ag_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_hadr_distributed_ag_replica
ms.assetid: a1e5f9cb-c350-4bb4-a04f-7394f6f25d62
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 780fb8e20efd3b8d40ed88c2382cbfdc01852b05
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sysfnhadrdistributedagreplica-transact-sql"></a>Sys.fn_hadr_distributed_ag_replica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Utilisé pour mapper un réplica dans un groupe de disponibilité distribué au groupe de disponibilité local.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_hadr_distributed_ag_replica( lag_Id, replica_id )  
```  
  
## <a name="arguments"></a>Arguments  
 '*lag_Id*'  
 Est l’identificateur du groupe de disponibilité distribués. *lag_Id* est de type **uniqueidentifier**.  
  
 '*replica_id*'  
 Est l’identificateur d’un réplica dans le groupe de disponibilité distribué. *replica_id* est de type **uniqueidentifier**.  
  
## <a name="tables-returned"></a>Tables retournées  
 Retourne les informations suivantes.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Identificateur unique (GUID) du groupe de disponibilité local.|  
  
## <a name="examples"></a>Exemples  
  
### <a name="using-sysfnhadrdistributedagreplica"></a>À l’aide de sys.fn_hadr_distributed_ag_replica  
 L’exemple suivant retourne une table avec l’identificateur de groupe de disponibilité local qui est associé avec le groupe de disponibilité distribué spécifié et le réplica.  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @replicaId uniqueidentifier = 'D5517513-04A8-FD82-14C6-E684EC913935'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_replica(@lagId, @replicaId)  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de groupes de disponibilité AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Groupes de disponibilité AlwaysOn & #40 ; SQL Server & #41 ;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Groupes de disponibilité de Distributed &#40;groupes de disponibilité AlwaysOn&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)  
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [GROUPE DE DISPONIBILITÉ ALTER &#40; Transact-SQL &#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
