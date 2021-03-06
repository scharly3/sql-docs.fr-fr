---
title: Sys.Schemas (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- schemas_TSQL
- sys.schemas_TSQL
- schemas
- sys.schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.schemas catalog view
ms.assetid: 29af5ce5-2af7-4103-8f08-3ec92603ba05
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 268a82b9470c189d2d2761e0ae6f81e56740c345
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="schemas-catalog-views---sysschemas"></a>Affichages - catalogue de schémas sys.schemas
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque schéma de base de données.  
  
> [!NOTE]  
>  Les schémas de base de données diffèrent des schémas XML, qui sont utilisés pour définir le modèle de contenu des documents XML.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du schéma. Unique dans la base de données.|  
|**schema_id**|**int**|Identificateur du schéma. Unique dans la base de données.|  
|**principal_id**|**int**|Identificateur du principal qui possède ce schéma.|  
  
## <a name="remarks"></a>Notes  
 Schémas de base de données agissent comme des espaces de noms ou des conteneurs d’objets, tels que des tables, vues, procédures et fonctions, qui se trouvent dans le **sys.objects** affichage catalogue.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue de schémas &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
