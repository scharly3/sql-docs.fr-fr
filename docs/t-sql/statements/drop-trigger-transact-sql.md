---
title: DROP TRIGGER (Transact-SQL) | Documents Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP TRIGGER
- DROP_TRIGGER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- renaming triggers
- triggers [SQL Server], removing
- DDL triggers, removing
- DROP TRIGGER statement
- deleting triggers
- dropping triggers
- removing triggers
- DML triggers, removing
ms.assetid: 092d0d71-9f1e-4e38-a1c4-2487adfa5b4e
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e3ca35b2b33a60d0af5dd31467f1381402f8f99b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-trigger-transact-sql"></a>DROP TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime un ou plusieurs déclencheurs DML ou DDL de la base de données active.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  
  
DROP TRIGGER [ IF EXISTS ] [schema_name.]trigger_name [ ,...n ] [ ; ]  
  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, REVOKE or UPDATE statement (DDL Trigger)  
  
DROP TRIGGER [ IF EXISTS ] trigger_name [ ,...n ]   
ON { DATABASE | ALL SERVER }   
[ ; ]  
  
-- Trigger on a LOGON event (Logon Trigger)  
  
DROP TRIGGER [ IF EXISTS ] trigger_name [ ,...n ]   
ON ALL SERVER  
```  

  
## <a name="arguments"></a>Arguments  
 *S’IL EXISTE*  
 **S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658), [!INCLUDE[sssds](../../includes/sssds-md.md)]).  
  
 Conditionnellement supprime le déclencheur uniquement s’il existe déjà.  
  
 *schema_name*  
 Nom du schéma auquel appartient le déclencheur DML. La portée des déclencheurs DML se limite au schéma de la table ou de la vue sur laquelle ils sont créés. *schema_name* ne peut pas être spécifié pour les déclencheurs DDL ou logon.  
  
 *trigger_name*  
 Indique le nom du déclencheur à supprimer. Pour afficher une liste des déclencheurs, utilisez [sys.server_assembly_modules](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) ou [sys.server_triggers](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md).  
  
 DATABASE  
 Indique que l'étendue du déclencheur DDL s'applique à la base de données active. L'argument DATABASE doit être spécifié s'il a également été indiqué lors de la création ou de la modification du déclencheur.  
  
 ALL SERVER  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indique que l'étendue du déclencheur DDL s'applique au serveur actif. L'argument ALL SERVER doit être spécifié s'il a également été indiqué lors de la création ou de la modification du déclencheur. ALL SERVER s'applique également aux déclencheurs de connexion.  
  
> [!NOTE]  
>  Cette option n'est pas disponible dans une base de données à relation contenant-contenu.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez éliminer un déclencheur DML en le supprimant ou en supprimant sa table. Lorsqu'une table est supprimée, tous les déclencheurs associés sont également supprimés.  
  
 Lorsqu’un déclencheur est supprimé, les informations sur le déclencheur sont supprimées de la **sys.objects**, **sys.triggers** et **sys.sql_modules** affichages catalogue.  
  
 Il est possible de supprimer plusieurs déclencheurs DDL avec une seule instruction DROP TRIGGER, uniquement s'ils ont tous été créés à l'aide de clauses ON identiques.  
  
 Pour renommer un déclencheur, utilisez DROP TRIGGER et CREATE TRIGGER. Pour modifier la définition d'un déclencheur, utilisez ALTER TRIGGER.  
  
 Pour plus d’informations sur la définition des dépendances d’un déclencheur spécifique, consultez [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md), [sys.dm_sql_referenced_entities &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md), et [sys.dm_sql_referencing_entities &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md).  
  
 Pour plus d’informations sur l’affichage du texte du déclencheur, consultez [sp_helptext &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md) et [sys.sql_modules &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
 Pour plus d’informations sur l’affichage d’une liste des déclencheurs existants, consultez [sys.triggers &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) et [sys.server_triggers &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Pour supprimer un DML trigger nécessite l’autorisation ALTER sur la table ou vue sur laquelle le déclencheur est défini.  
  
 La suppression d'un déclencheur DDL défini avec une étendue de serveur (ON ALL SERVER) ou d'un déclencheur de connexion nécessite l'autorisation CONTROL SERVER sur le serveur. La suppression d'un déclencheur DDL défini avec une étendue de base de données (ON DATABASE) nécessite une autorisation ALTER ANY DATABASE DDL TRIGGER sur la base de données active.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-dropping-a-dml-trigger"></a>A. Suppression d'un déclencheur DML  
 L'exemple suivant supprime le déclencheur `employee_insupd` de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. (À partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] vous pouvez utiliser la syntaxe DROP TRIGGER IF EXISTS.)  
  
```  
IF OBJECT_ID ('employee_insupd', 'TR') IS NOT NULL  
   DROP TRIGGER employee_insupd;  
```  
  
### <a name="b-dropping-a-ddl-trigger"></a>B. Suppression d'un déclencheur DDL  
 L'exemple suivant supprime le déclencheur DDL `safety`.  
  
> [!IMPORTANT]  
>  Étant donné que les déclencheurs DDL ne sont pas étendus aux schémas et, par conséquent, n’apparaissent pas dans le **sys.objects** catalogue vue, la fonction OBJECT_ID ne peut pas être utilisée pour déterminer s’ils existent dans la base de données. Les objets qui ne sont pas compris dans l'étendue du schéma doivent être interrogés à l'aide de l'affichage catalogue approprié. Pour les déclencheurs DDL, utilisez **sys.triggers**.  
  
```  
DROP TRIGGER safety  
ON DATABASE;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Obtenir des informations sur les déclencheurs DML](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  
