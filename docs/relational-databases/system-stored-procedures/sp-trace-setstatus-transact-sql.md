---
title: sp_trace_setstatus (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_trace_setstatus_TSQL
- sp_trace_setstatus
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setstatus
ms.assetid: 29e7a7d7-b9c1-414a-968a-fc247769750d
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a6f6aacf619df24477528b4d39ad9551be321e61
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sptracesetstatus-transact-sql"></a>sp_trace_setstatus (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie l'état actuel de la trace spécifiée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt des événements étendus.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_trace_setstatus [ @traceid = ] trace_id , [ @status = ] status  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@traceid=** ] *trace_id*  
 ID de la trace à modifier. *l’argument trace_id* est **int**, sans valeur par défaut. L’utilisateur emploie cette *trace_id* valeur pour identifier, modifier et contrôler la trace. Pour plus d’informations sur la récupération de la *trace_id*, consultez [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md).  
  
 [  **@status=** ] *état*  
 Indique l'action à implémenter sur la trace. *état* est **int**, sans valeur par défaut.  
  
 Le tableau ci-après répertorie les états qui peuvent être spécifiés.  
  
|État| Description|  
|------------|-----------------|  
|**0**|Arrête la trace spécifiée.|  
|**1**|Démarre la trace spécifiée.|  
|**2**|Ferme la trace spécifiée et supprime sa définition du serveur.|  
  
> [!NOTE]  
>  Une trace doit d'abord être arrêtée avant d'être fermée. de la même façon qu'elle doit d'abord être arrêtée et fermée avant de pouvoir être consultée.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Le tableau suivant décrit les valeurs de code que les utilisateurs peuvent recevoir à la fin de l'exécution de la procédure stockée.  
  
|Code de retour| Description|  
|-----------------|-----------------|  
|**0**|Aucune erreur.|  
|**1**|Erreur inconnue.|  
|**8**|L'état spécifié n'est pas valide.|  
|**9**|Le descripteur de trace spécifié n'est pas valide.|  
|**13**|Mémoire insuffisante. Renvoyé lorsqu'il n'y a pas assez de mémoire pour exécuter l'action spécifiée.|  
  
 Si la trace est déjà dans l’état spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournera **0**.  
  
## <a name="remarks"></a>Notes  
 Les paramètres de Trace de SQL toutes les procédures stockées (**sp_trace_xx**) sont de type strict. Si ces paramètres ne sont pas appelés avec des types de données appropriés pour les paramètres d'entrée tels qu'ils sont spécifiés dans la description de l'argument, la procédure stockée renvoie une erreur.  
  
 Pour obtenir un exemple d’utilisation de procédures stockées de trace, consultez [Créer une trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 L'utilisateur doit disposer de l'autorisation ALTER TRACE.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [Trace SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
