---
title: Sys.plan_guides (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.planguides_TSQL
- plan_guides
- sys.planguides
- plan_guides_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.plan_guides catalog view
ms.assetid: 3dde0397-ef6f-4b3f-8250-3f25584eb62b
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b1ae6cfc3e52e970ff4c2aecc825394fc3f975b6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sysplanguides-transact-sql"></a>sys.plan_guides (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contient une ligne pour chaque repère de plan dans la base de données.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**plan_guide_id**|**int**|Identificateur unique du repère de plan dans la base de données.|  
|**nom**|**sysname**|Nom du repère de plan.|  
|**create_date**|**datetime**|Date et heure de création du repère de plan.|  
|**modify_date**|**DateTime**|Date de la dernière modification du repère de plan.|  
|**is_disabled**|**bit**|1 = Repère de plan désactivé.<br /><br /> 0 = Repère de plan activé.|  
|**query_text**|**nvarchar(max)**|Texte de la requête utilisé pour créer le repère de plan.|  
|**scope_type**|**tinyint**|Identifie l'étendue du repère de plan.<br /><br /> 1 = OBJECT<br /><br /> 2 = SQL<br /><br /> 3 = TEMPLATE|  
|**scope_type_desc**|**nvarchar(60)**|Description de l'étendue du repère de plan.<br /><br /> OBJECT<br /><br /> SQL<br /><br /> TEMPLATE|  
|**scope_object_id**|**Int**|object_id de l'objet définissant l'étendue du repère de plan, si celle-ci est OBJECT.<br /><br /> NULL si le repère de plan ne s'étend pas à OBJECT.|  
|**scope_batch**|**nvarchar(max)**|Texte du traitement, si **scope_type** est SQL.<br /><br /> NULL si le type du traitement n'est pas SQL.<br /><br /> Si la valeur NULL et **scope_type** SQL, la valeur de **query_text** s’applique.|  
|**parameters**|**nvarchar(max)**|Chaîne définissant la liste des paramètres associés au repère de plan.<br /><br /> NULL = Aucune liste de paramètres n'est associée au repère de plan.|  
|**indicateurs**|**nvarchar(max)**|Indicateurs de la clause OPTION associés au repère de plan.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
