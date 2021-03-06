---
title: Conformité SQL-92 | Documents Microsoft
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
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 09b1a044a362207b5bc1c04d3a90e210ad7c8137
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sql-92-compliance"></a>Conformité SQL-92
Les pilotes de base de données ODBC Desktop et le moteur Microsoft Jet sous-jacente ne sont pas conformes SQL-92. Ils prennent en charge de nombreuses fonctionnalités qui ont été définies dans SQL-92. Certaines fonctionnalités prises en charge dans le pilote ne sont pas pris en charge dans SQL-92. Pour plus d’informations, consultez la *Guide du programmeur moteur Microsoft Jet de base de données*. Voici les principales différences entre les deux :  
  
-   Le SQL utilisé par les pilotes de la base de données Desktop prend en charge des expressions plus puissantes que ceux spécifiés par SQL-92.  
  
-   Différentes règles s’appliquent au prédicat BETWEEN.  
  
-   Le SQL utilisé par les pilotes de base de données de bureau et ANSI SQL prend en charge les mots clés différents.  
  
 Les fonctionnalités de SQL-92 suivantes ne sont pas pris en charge par Microsoft Jet SQL :  
  
-   Instructions de sécurité, telles que l’allocation et de verrouillage.  
  
-   DISTINCT avec les références de fonction d’agrégation.  
  
 Les fonctionnalités suivantes sont des améliorations dans le SQL utilisé par les pilotes de base de données de bureau qui ne sont pas spécifiés par SQL-92 :  
  
-   L’instruction TRANSFORM est prise en charge pour les requêtes d’analyse croisée.  
  
-   Fonctions d’agrégation supplémentaires (**StDev** et **VarP**).  
  
> [!NOTE]  
>  Les pilotes de la base de données Desktop prend en charge la syntaxe ANSI standard (pourcentage) et _ (trait de soulignement), pas * (astérisque) et ? (point d’interrogation).
