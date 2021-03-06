---
title: "Créer et exécuter des traces à l’aide de procédures stockées Transact-SQL | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-trace
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c5a55fc6c2b8af7d93997db13497f9320bf3669
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="create-and-run-traces-using-transact-sql-stored-procedures"></a>Créer et exécuter des traces à l'aide de procédures stockées Transact-SQL.
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le processus de trace à l'aide de la trace SQL varie en fonction de la façon dont vous avez créé et exécuté votre trace, à savoir au moyen du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] de Microsoft ou via les procédures stockées système.  
  
 Une alternative au [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]est représentée par les procédures stockées système [!INCLUDE[tsql](../../includes/tsql-md.md)] qui permettent de créer et d'exécuter des traces. La procédure de trace à l'aide des procédures stockées système est la suivante :  
  
1.  Créez une trace en exécutant **sp_trace_create**.  
  
2.  Ajoutez des événements à l’aide de **sp_trace_setevent**.  
  
3.  (Facultatif) Définissez un filtre avec **sp_trace_setfilter**.  
  
4.  Démarrez la trace avec **sp_trace_setstatus**.  
  
5.  Arrêtez la trace avec **sp_trace_setstatus**.  
  
6.  Fermez la trace avec **sp_trace_setstatus**.  
  
    > [!NOTE]  
    >  L'utilisation des procédures stockées système [!INCLUDE[tsql](../../includes/tsql-md.md)] crée une trace serveur qui garantit qu'aucun événement ne sera perdu aussi longtemps qu'il restera de la place sur le disque et qu'aucune erreur d'écriture ne se produira. Si le disque est plein ou s'il présente une défaillance, l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] continuera à s'exécuter, mais la trace s'arrêtera. Si l'option **c2 audit mode** est définie et qu'il se produit une erreur d'écriture, la trace cesse et l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'arrête. Pour plus d’informations sur le paramètre **Mode d’audit c2** , consultez [Mode d’audit C2 (option de configuration de serveur)](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Optimiser Trace SQL](../../relational-databases/sql-trace/optimize-sql-trace.md)|Contient des informations sur les manières de réduire les effets de la trace sur les performances du système.|  
|[Filtrer une trace](../../relational-databases/sql-trace/filter-a-trace.md)|Contient des informations sur l'utilisation de filtres pour la trace.|  
|[Limiter les tailles de fichier et de table de trace](../../relational-databases/sql-trace/limit-trace-file-and-table-sizes.md)|Contient des informations sur la façon de limiter la taille des fichiers et des tables où les données de trace sont écrites. Notez que seul le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] peut écrire les données de trace dans des tables.|  
|[Planifier les traces](../../relational-databases/sql-trace/schedule-traces.md)|Contient des informations sur la façon de définir l'heure de démarrage et l'heure de fin de la trace.|  
  
## <a name="see-also"></a> Voir aussi  
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  
