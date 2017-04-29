---
title: "MSSQL_ENG002627 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG002627 (erreur)"
ms.assetid: 7f4136ac-3784-4a41-a98c-8a02308e4883
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG002627
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2627|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique|Néant|  
|Texte du message|Violation de %1! contrainte '%2!'. Impossible d’insérer une clé en double dans l’objet ' %.\*%.*ls.|  
  
## Explication  
 C'est une erreur générale qui peut être déclenchée qu'une base de données soit répliquée ou non. Dans les bases de données répliquées, l'erreur est généralement déclenchée car les clés primaires n'ont pas été gérés de manière appropriée à travers la topologie. Dans un environnement distribué, il est primordial de s'assurer que la même valeur n'est pas insérée dans une colonne de clé primaire ou toute autre colonne unique sur plus d'un seul nœud. Les raisons peuvent être les suivantes :  
  
-   Les insertions et mises à jour sur une ligne se produisent sur plus d'un seul nœud. La réplication de fusion et les abonnements pouvant être mis à jour pour la réplication transactionnelle permettent tous deux la détection et la résolution des conflits, mais il est quand même préférable de n'insérer ou de ne mettre à jour une ligne donnée que sur un seul nœud. La réplication transactionnelle d'égal à égal ne permet pas la détection et la résolution des conflits, elle nécessite que les insertions et mises à jour soient partitionnées.  
  
-   Une ligne a été insérée sur un abonné qui devrait être en lecture seule. Les abonnés aux publications d'instantanés, ainsi que les abonnés au publications transactionnelles devraient être traités comme étant en lecture seule à moins d'utiliser des abonnements pouvant être mis à jour ou la réplication transactionnelle d'égal à égal.  
  
-   Une table avec une colonne d'identité est utilisée, mais la colonne n'est par gérée de façon appropriée.  
  
## Action de l'utilisateur  
 L'action requise dépend de la raison du déclenchement de l'erreur :  
  
-   Les insertions et mises à jour sur une ligne se produisent sur plus d'un seul nœud.  
  
     Quel que soit le type de réplication utilisé, il est recommandé de partitionner les insertions et mises à jour chaque fois que cela est possible, car cela réduit le traitement nécessaire pour la détection et la résolution des conflits. Pour la réplication transactionnelle d'égal à égal, le partitionnement d'insertions et de mises à jour est nécessaire. Pour plus d’informations, consultez [égal à la réplication transactionnelle](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
-   Une ligne a été insérée sur un abonné qui devrait être en lecture seule.  
  
     N'insérez pas ou ne mettez pas à jour de lignes sur l'Abonné à moins d'utiliser la réplication de fusion, la réplication transactionnelle avec abonnements pouvant être mis à jour ou la réplication transactionnelle d'égal à égal.  
  
-   Une table avec une colonne d'identité est utilisée, mais la colonne n'est par gérée de façon appropriée.  
  
     Pour la réplication de fusion et la réplication transactionnelle avec abonnements pouvant être mis à jour, les colonnes d'identité doivent être gérées automatiquement par la réplication. Pour la réplication transactionnelle d'égal à égal, elles doivent être gérées manuellement. Pour plus d’informations, consultez [répliquer les colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Réplication de fusion](../../relational-databases/replication/merge/merge-replication.md)   
 [Réplication transactionnelle d'égal à égal](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  