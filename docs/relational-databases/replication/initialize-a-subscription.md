---
title: Initialiser un abonnement | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 703a1aedae5a16236fe64c087dee9ed81667e9c3
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="initialize-a-subscription"></a>Initialiser un abonnement
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les Abonnés dans une topologie de réplication doivent être initialisés, de façon à ce qu'ils aient une copie du schéma de chaque article de la publication à laquelle ils se sont abonnés et tous les objets de réplication requis, tels que des procédures stockées, des déclencheurs et des tables de métadonnées. De plus, l'Abonné reçoit généralement un jeu de données initial. La méthode d'initialisation par défaut utilise un instantané complet qui comprend le schéma, les objets de réplication et des données, mais les publications peuvent aussi être initialisées sans instantané complet.  
  
 Pour plus d'informations, consultez [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) et [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
