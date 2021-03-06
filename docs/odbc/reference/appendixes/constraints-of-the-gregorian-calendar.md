---
title: Contraintes du calendrier grégorien | Documents Microsoft
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
- data types [ODBC], Gregorian calendar
- Gregorian calendar [ODBC]
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 36cbe4802912e2497408498b32e48f8f201479f1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="constraints-of-the-gregorian-calendar"></a>Contraintes du calendrier grégorien
Types de données date et datetime et que les champs à droite de types de données interval, doivent être conforme aux contraintes du calendrier grégorien. Ces contraintes sont les suivantes :  
  
-   La valeur du champ mois doit être compris entre 1 et 12, inclus.  
  
-   La valeur du champ jour doit être comprise entre 1 et le nombre de jours du mois. Le nombre de jours du mois est déterminé à partir des valeurs des champs année et mois et peut être 28, 29, 30 ou 31. (Le nombre de jours du mois peut également dépendre s’il s’agit d’une année bissextile.)  
  
-   La valeur du champ heures doit être comprise entre 0 et 23 inclus.  
  
-   La valeur du champ minute doit être comprise entre 0 et 59, inclus.  
  
-   Pour la fin du champ des secondes de types de données interval, la valeur du champ secondes doit être comprise entre 0 et 59,9 (*n*), inclusivement, où *n* est le nombre de chiffres de précision en fractions de seconde.  
  
-   Pour la fin du champ des secondes de types de données datetime, la valeur du champ secondes doit être comprise entre 0 et 61.9 (*n*), inclusivement, où *n* Spécifie le nombre de chiffres « 9 » et la valeur de *n*  précision en fractions de seconde. (La plage des secondes permet à deux secondes intercalaires maintenir la synchronisation de temps de sidereal.)
