---
title: Propriétés de SQL Server Agent (page Historique) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0da07d6c02c070f4819b2fd5758755992aa9c71d
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2018
---
# <a name="sql-server-agent-properties-history-page"></a>Propriétés de l'Agent SQL Server (page Historique)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher et modifier des paramètres de gestion du journal d'historique du service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Options  
**Limiter la taille du journal d'historique des travaux.**  
Limite la quantité d'informations d'historique des travaux que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] conserve dans le journal.  
  
**Taille maximale du journal d'historique des travaux (lignes)**  
Spécifie le nombre maximal de lignes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] conserve. Lorsque le journal a atteint le nombre de lignes indiqué, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] supprime les lignes les plus anciennes à mesure que de nouvelles lignes sont insérées.  
  
**Nombre  maximal de lignes d'historique des travaux par travail**  
Spécifie le nombre maximal de lignes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] conserve par travail. Lorsque l'historique d'un travail particulier a atteint le nombre de lignes indiqué, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] supprime les lignes les plus anciennes à mesure que de nouvelles lignes sont insérées.  
  
**Supprimer l'historique de l'agent**  
Indique que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] va supprimer les entrées présentes dans le journal depuis plus longtemps que la période spécifiée. Il s'agit d'une exécution ponctuelle pour supprimer l'historique. Si vous préférez un travail récurrent, créez et planifiez un plan de maintenance avec un travail de nettoyage.  
  
**Antérieur à**  
Spécifie la période pendant laquelle l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] conserve les entrées.  
  
## <a name="see-also"></a> Voir aussi  
[Journal des erreurs de l'Agent SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
