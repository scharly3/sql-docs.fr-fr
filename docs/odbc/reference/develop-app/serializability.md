---
title: La capacité à sérialiser | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transaction isolation [ODBC]
- transactions [ODBC], serialization
- serialization [ODBC]
- transactions [ODBC], isolation
ms.assetid: 142e4ac0-2977-4a2b-96ae-c9e5bd2c448a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aa983da3ad05b6f4c4ac29fbdf986a7a8a350e34
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="serializability"></a>Sérialisation
Dans l’idéal, les transactions doivent être *sérialisable*. Les transactions sont dites sérialisables si les résultats de l’exécution de transactions simultanément sont les mêmes que les résultats de leur exécution en série : autrement dit, une après l’autre. Il n’est pas important de la transaction s’exécute en premier, uniquement que le résultat ne reflète pas les mélanger des transactions.  
  
 Par exemple, supposons que la transaction A multiplie les valeurs de données par 2 et la transaction B ajoute 1 aux valeurs de données. Supposons qu’il n’y a deux valeurs de données : 0 et 10. Si ces transactions sont exécutées une après l’autre, les nouvelles valeurs seront 1 et 21 si la transaction A est exécutée en premier lieu, ou 2 et 22 si la transaction B est exécutée en premier. Mais que se passe-t-il si l’ordre dans lequel les deux transactions sont exécutées est différent pour chaque valeur ? Si la transaction Qu'a est exécuté en premier sur la première valeur et la transaction B sont exécutés en premier sur la deuxième valeur, les nouvelles valeurs sont 1 et 22. Si cet ordre est inversé, les nouvelles valeurs sont 2 et 21. Les transactions sont sérialisables si 1, 21 et 2, 22 sont les résultats seulement possibles. Les transactions ne sont pas sérialisable si 1, 22 ou 2, 21 est un résultat possible.  
  
 Par conséquent, pourquoi est renouvelable souhaitable ? En d’autres termes, pourquoi est-ce important qu’il apparaît qu’une transaction se termine avant le démarrage de la transaction suivante ? Prenez le problème suivant. Un représentant commercial est saisie de commandes en même temps qu'un employé envoie des factures. Supposons que le représentant commercial entre une commande à partir de la société X, mais ne la valide pas ; le représentant commercial toujours communique avec le représentant à partir de la société X. Le régisseur de demande une liste de toutes les commandes ouvertes et détecte l’ordre de la société X et les envoie une facture. Maintenant le représentant de la société X décide qu'ils souhaitent modifier leur ordre, de sorte que si le représentant commercial il change avant de valider la transaction. Société X Obtient une facture incorrecte.  
  
 Si du représentant commercial et du régisseur de transactions ont été sérialisables, ce problème ne serait jamais survenus. Soit les transactions entre le commercial sont terminés avant le début de la transaction de l’employé, auquel cas le régisseur sera donc avoir envoyé la facture de façon correcte, ou les transactions de l’employé sont terminés avant la transaction entre le commercial démarré, auquel cas le régisseur n'aurait pas envoyé une facture à la société X tout.
