---
title: Le suivi des modifications de fonctions (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/08/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- functions [SQL Server], change tracking
- change tracking [SQL Server], functions
ms.assetid: 04eb53c4-8b69-414e-9696-185d227fea35
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6967dfb85baa59aa563bb054a6de62756e16bf2f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="change-tracking-functions-transact-sql"></a>Fonctions de suivi des modifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Les enregistrements de suivi des modifications insèrent, mettent à jour et suppriment les activités appliquées aux tables faisant l'objet d'un suivi, en fournissant les détails des modifications dans un format relationnel simple à utiliser. Les fonctions suivantes retournent des informations sur les modifications.  
  
|Fonction| Description|  
|--------------|-----------------|  
|[CHANGETABLE (CHANGES)](../../relational-databases/system-functions/changetable-transact-sql.md)|Retourne les informations de suivi de toutes les modifications apportées à une table depuis une version spécifiée.|  
|[FONCTION CHANGETABLE (VERSION)](../../relational-databases/system-functions/changetable-transact-sql.md)|Retourne les informations de suivi des modifications les plus récentes pour une ligne spécifiée.|  
|[CHANGE_TRACKING_MIN_VALID_VERSION()](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|Retourne la version minimale valide pour l’utilisation de l’obtention des informations de suivi à partir de la table spécifiée lorsque vous utilisez la [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) (fonction).|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|Obtient une version associée à la dernière transaction validée. Vous pouvez utiliser cette version de la prochaine fois que vous énumérez des modifications à l’aide de CHANGETABLE.|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|Interprète la valeur SYS_CHANGE_COLUMNS retournée par la fonction CHANGETABLE(CHANGES ...).|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|Active la spécification d'un contexte de modification, tel qu'un ID d'appelant, lorsqu'une application modifie des données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Suivi des modifications de données &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  