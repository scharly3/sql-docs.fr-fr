---
title: sp_purge_jobhistory (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_purge_jobhistory_TSQL
- sp_purge_jobhistory
dev_langs: TSQL
helpviewer_keywords: sp_purge_jobhistory
ms.assetid: 237f9bad-636d-4262-9bfb-66c034a43e88
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8e9706f38a69343ca68000d85d12869b965e2cd3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sppurgejobhistory-transact-sql"></a>sp_purge_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Supprime les enregistrements d'historique d'un travail.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_purge_jobhistory   
   {   [ @job_name = ] 'job_name' |   
     | [ @job_id = ] job_id }  
   [ , [ @oldest_date = ] oldest_date ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_name=** ] **'***job_name***'**  
 Nom du travail dont il faut supprimer les enregistrements d'historique. *job_name*est **sysname**, avec NULL comme valeur par défaut. Soit *job_id* ou *job_name* doit être spécifié, mais ne peut pas être spécifiés.  
  
> [!NOTE]  
>  Membres de la **sysadmin** rôle serveur fixe ou les membres de la **SQLAgentOperatorRole** du rôle de base de données fixe peut exécuter **sp_purge_jobhistory** sans spécifier un *job_name* ou *job_id*. Lorsque **sysadmin** les utilisateurs ne spécifient pas de ces arguments, l’historique des travaux pour tous les travaux locaux et multiserveurs est supprimé dans le délai spécifié par *oldest_date*. Lorsque **SQLAgentOperatorRole** les utilisateurs ne spécifient pas de ces arguments, l’historique des travaux pour tous les travaux locaux est supprimé dans le délai spécifié par *oldest_date*.  
  
 [  **@job_id=** ] *job_id*  
 Numéro d'identification du travail dont les enregistrements doivent être supprimés. *job_id*est **uniqueidentifier**, avec NULL comme valeur par défaut. Soit *job_id* ou *job_name* doit être spécifié, mais ne peut pas être spécifiés. Consultez la note dans la description de  **@job_name**  pour plus d’informations sur la façon **sysadmin** ou **SQLAgentOperatorRole** les utilisateurs peuvent utiliser cet argument.  
  
 [  **@oldest_date**  =] *oldest_date*  
 Enregistrement le plus ancien à conserver dans l'historique. *l’argument oldest_date* est **datetime**, avec NULL comme valeur par défaut. Lorsque *oldest_date* est spécifié, **sp_purge_jobhistory** supprime uniquement les enregistrements qui sont antérieurs à la valeur spécifiée.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="remarks"></a>Notes  
 Lorsque **sp_purge_jobhistory** se termine correctement, un message est retourné.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, seuls les membres de la **sysadmin** rôle serveur fixe ou **SQLAgentOperatorRole** du rôle de base de données fixes peuvent exécuter cette procédure stockée. Membres de **sysadmin** peuvent purger l’historique des travaux pour tous les travaux locaux et multiserveurs. Membres de **SQLAgentOperatorRole** peuvent purger l’historique des travaux pour tous les travaux locaux.  
  
 Autres utilisateurs, y compris les membres de **SQLAgentUserRole** et les membres de **SQLAgentReaderRole**, doit être accordé explicitement l’autorisation EXECUTE sur **sp_purge_jobhistory**. Une fois l'autorisation accordée sur cette procédure stockée, ces utilisateurs peuvent uniquement supprimer l'historique des travaux dont ils sont propriétaires.  
  
 Le **SQLAgentUserRole**, **SQLAgentReaderRole**, et **SQLAgentOperatorRole** sont des rôles de base de données fixe dans le **msdb** base de données. Pour plus d’informations sur les autorisations, consultez [SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-remove-history-for-a-specific-job"></a>A. Suppression de l'historique d'un travail spécifique  
 L'exemple suivant supprime l'historique du travail `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-remove-history-for-all-jobs"></a>B. Suppression de l'historique de tous les travaux  
  
> [!NOTE]  
>  Seuls les membres de la **sysadmin** fixe le rôle de serveur et les membres de la **SQLAgentOperatorRole** peuvent supprimer l’historique de tous les travaux. Lorsque **sysadmin** utilisateurs exécutent cette procédure stockée sans paramètres, l’historique des travaux pour tous les travaux locaux et multiserveurs est systématiquement purgé. Lorsque **SQLAgentOperatorRole** utilisateurs exécutent cette procédure stockée sans paramètres, seulement l’historique des travaux pour tous les travaux locaux est purgée.  
  
 Dans cet exemple, la procédure est exécutée sans paramètres pour supprimer tous les enregistrements d'historique.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_help_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobhistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [ACCORDER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
  