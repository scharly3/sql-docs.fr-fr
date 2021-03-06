---
title: DAY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 444df60a2cfe3adae045020b3db8d673946dccb1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne un entier représentant le jour (jour du mois) de la *date* spécifiée.
  
Pour obtenir une vue d’ensemble de tous les types de données et fonctions de date et d’heure [!INCLUDE[tsql](../../includes/tsql-md.md)], consultez [Types de données et fonctions de date et d’heure &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>Arguments  
*date*  
Expression qui peut être résolue en une valeur **time**, **date**, **smalldatetime**, **datetime**, **datetime2** ou **datetimeoffset**. L’argument *date* peut être une expression, une expression de colonne, une variable définie par l’utilisateur ou un littéral de chaîne.
  
## <a name="return-type"></a>Type de retour  
**Int**
  
## <a name="return-value"></a>Valeur retournée  
DAY retourne la même valeur que [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**day**, *date*).
  
Si *date* contient uniquement une partie heure, la valeur renvoyée est 1, le jour de base.
  
## <a name="examples"></a>Exemples  
L'instruction suivante retourne `30`. Il s'agit du numéro du jour.
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
L'instruction suivante retourne `1900, 1, 1`. L’argument pour *date* est le chiffre `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprète `0` comme le 1er janvier 1900.
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


