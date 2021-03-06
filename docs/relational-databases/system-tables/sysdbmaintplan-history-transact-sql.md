---
title: sysdbmaintplan_history (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c0c42b7c455c0bcbb08913bbe5ae88422e7cace7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sysdbmaintplanhistory-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette table est stockée dans le **msdb** base de données.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|Séquence de l'historique effectué par les plans de maintenance de la base de données.|  
|**plan_id**|**uniqueidentifier**|Identificateur du plan de maintenance de la base de données.|  
|**plan_name**|**sysname**|Nom du plan de maintenance de base de données.|  
|**database_name**|**sysname**|Nom de la base de données associée au plan de maintenance de base de données.|  
|**server_name**|**sysname**|Nom système.|  
|**Activité**|**nvarchar(128)**|Activité réalisée par le plan de maintenance de la base de données (par exemple, sauvegarde du journal des transactions).|  
|**succeeded**|**bit**|**0** = réussite **1** = Échec|  
|**end_time**|**datetime**|Heure de la fin de l'exécution de l'action.|  
|**duration**|**int**|Durée nécessaire à l'exécution de l'action du plan de maintenance de la base de données.|  
|**start_time**|**datetime**|Heure de début de l'action.|  
|**error_number**|**int**|Numéro d'erreur indiqué lors d'un échec.|  
|**message**|**nvarchar(512)**|Message généré par **sqlmaint**.|  
  
  
