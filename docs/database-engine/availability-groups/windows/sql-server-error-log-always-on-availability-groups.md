---
title: Journal des erreurs SQL Server (groupes de disponibilité Always On) (SQL Server) | Microsoft Docs
ms.custom: ag-guide
ms.date: 06/13/2017
ms.prod: sql-server-2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39d0c98d-75af-4dd1-b908-30d31af56f2a
caps.latest.revision: 4
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 535e8612c3b569a7dfcd9bbe88572e0fdc8c1f29
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2018
---
# <a name="sql-server-error-log-always-on-availability-groups"></a>Journal des erreurs SQL Server (groupes de disponibilité Always On)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le journal des erreurs SQL Server signale les événements qui affectent les groupes de disponibilité Always On, notamment :  
  
-   Communication avec le cluster WSFC (clustering de basculement Windows Server)  
  
-   Transitions d’état des réplicas de disponibilité  
  
-   Transitions d’état des bases de données de disponibilité  
  
-   État de connectivité des bases de données de disponibilité entre les réplicas principal et secondaire  
  
-   États des points de terminaison de groupe de disponibilité  
  
-   États des écouteurs de groupe de disponibilité  
  
-   État du bail entre la DLL de ressource SQL Server (en cours d’exécution dans le cluster WSFC) et l’instance SQL Server (pour plus d’informations, consultez [Fonctionnement : délai d’expiration de bail Always On SQL Server](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-alwayson-lease-timeout.aspx))  
  
-   Événements d’erreur dans le groupe de disponibilité  


Les symptômes suivants doivent vous inciter à passer en revue le journal des erreurs SQL Server :  

-   Impossibilité d’accéder aux bases de données de disponibilité  
  
-   Basculement inattendu du groupe de disponibilité  
  
-   État Résolution affecté de manière inattendue au groupe de disponibilité  
  
-   Groupe de disponibilité dans un état indéterminé  
  
Pour plus d’informations, consultez [Afficher le journal des erreurs SQL Server &#40;SQL Server Management Studio&#41;](~/relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md).  
  
  