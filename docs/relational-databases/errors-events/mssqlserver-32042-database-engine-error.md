---
title: MSSQLSERVER_32042 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 32042 (Database Engine error)
ms.assetid: 53a51c7a-dcd4-4c15-b4d2-6aaa9dce76da
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 565be96fc2300d7a54b3d98ec0f2564e424a49cc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver32042"></a>MSSQLSERVER_32042
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|32042|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum32042|  
|Texte du message|L'alerte relative au journal non envoyé s'est déclenchée. La valeur actuelle de '%d' dépasse le seuil '%d'.|  
  
## <a name="explanation"></a>Explication  
Cet événement de mise en miroir de bases de données est émis sur l'instance du serveur principal pour indiquer que la quantité de journal non envoyé a atteint la valeur de seuil définie par l'utilisateur. En règle générale, cet événement se produit car les performances du système ont changé. Soit la bande passante entre les deux systèmes a diminué, soit la charge a augmenté.  
  
La quantité de journal non envoyé est une mesure de performance qui peut vous aider à évaluer le risque de perte de données exprimé en kilo-octets (Ko) de journal non envoyé. Cette mesure s’avère particulièrement appropriée pour les sessions en mode hautes performances. Toutefois, elle est également adaptée aux sessions en mode haute sécurité lorsque la mise en miroir est interrompue ou suspendue suite à une déconnexion des serveurs partenaires.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez les charges incombant aux instances du serveur principal et du serveur miroir et à leur connexion réseau pour déterminer la cause du problème.  
  
## <a name="see-also"></a>Voir aussi  
[Mise en miroir de bases de données &#40;SQL Server&#41;](~/database-engine/database-mirroring/database-mirroring-sql-server.md)  
[Utiliser des seuils d’avertissement et d’alertes sur des métriques de performances de mise en miroir &#40;SQL Server&#41;](~/database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
