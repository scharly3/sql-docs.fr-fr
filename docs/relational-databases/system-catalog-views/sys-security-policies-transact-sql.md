---
title: Sys.security_policies (Transact-SQL) | Documents Microsoft
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
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- SYS.SECURITY_POLICIES_TSQL
- SECURITY_POLICIES_TSQL
- SYS.SECURITY_POLICIES
- SECURITY_POLICIES
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_policies catalog view
- security_policies catalog view
ms.assetid: 35362f5b-e601-4049-9e1d-c5307e823831
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6b588dcf21742dac41c9501bf165f7f9df04da62
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="syssecuritypolicies-transact-sql"></a>Sys.security_policies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque stratégie de sécurité dans la base de données.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Nom de la stratégie de sécurité, unique dans la base de données.|  
|object_id|**int**|ID de la stratégie de sécurité.|  
|principal_id|**int**|ID du propriétaire de la stratégie de sécurité, tel qu'enregistré dans la base de données. NULL si le propriétaire est déterminé par le schéma.|  
|schema_id|**int**|ID du schéma où réside l'objet.|  
|parent_object_id|**int**|Identificateur de l'objet auquel appartient la stratégie. Doit être égal à 0.|  
|Type|**vachar(2)**|Doit être **SP**.|  
|type_desc|**nvarchar(60)**|**SECURITY_POLICY**.|  
|create_date|**datetime**|Date UTC de création de la stratégie de sécurité.|  
|modify_date|**datetime**|Date UTC de dernière modification de la stratégie de sécurité.|  
|is_ms_shipped|**bit**|Toujours false.|  
|is_enabled|**bit**|État de spécification de stratégie de sécurité :<br /><br /> 0 = désactivé<br /><br /> 1 = activé|  
|is_not_for_replication|**bit**|La stratégie a été créée avec l'option NOT FOR REPLICATION.|  
|uses_database_collation|**bit**|Utilise le même classement que la base de données.|  
|is_schemabinding_enabled|**bit**|État de la liaison au schéma pour la stratégie de sécurité :<br /><br /> 0 ou NULL = activé<br /><br /> 1 = désactivé|  
  
## <a name="permissions"></a>Autorisations  
 Les principaux avec le **ALTER ANY SECURITY POLICY** autorisation ont accès à tous les objets dans cet affichage catalogue, ainsi que toute personne ayant **VIEW DEFINITION** sur l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité au niveau des lignes](../../relational-databases/security/row-level-security.md)   
 [sys.security_predicates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
