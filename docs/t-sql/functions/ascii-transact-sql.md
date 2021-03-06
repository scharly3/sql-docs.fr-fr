---
title: ASCII (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ASCII_TSQL
- ASCII
dev_langs:
- TSQL
helpviewer_keywords:
- ASCII function
- characters [SQL Server], ASCII
- code [SQL Server], ASCII
- leftmost character of expression
ms.assetid: 45c2044a-0593-4805-8bae-0fad4bde2e6b
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 31edb66f5d213a7b2241f5f97d9733cb9e0cb523
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="ascii-transact-sql"></a>ASCII (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne la valeur du code ASCII du caractère situé le plus à gauche dans une expression de caractères.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
ASCII ( character_expression )  
```  
  
## <a name="arguments"></a>Arguments  
*expression_caractère*  
[Expression](../../t-sql/language-elements/expressions-transact-sql.md) de type **char** ou **varchar**.
  
## <a name="return-types"></a>Types de retour
 **Int**  
  
## <a name="remarks"></a>Notes 
ASCII est l’abréviation d’**A**merican **S**tandard **C**ode for **I**nformation **I**nterchange. Il s’agit d’une norme de codage de caractères pour les ordinateurs modernes. Consultez la section **Caractères imprimables** de la rubrique [ASCII](https://www.wikipedia.org/wiki/ASCII) pour obtenir la liste des caractères ASCII.

## <a name="examples"></a>Exemples  
Cet exemple considère un jeu de caractères ASCII et retourne la valeur `ASCII` de 6 caractères.
  
```sql
SELECT ASCII('A') AS A, ASCII('B') AS B,   
ASCII('a') AS a, ASCII('b') AS b,  
ASCII(1) AS [1], ASCII(2) AS [2];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
A           B           a           b           1           2  
----------- ----------- ----------- ----------- ----------- -----------  
65          66          97          98          49          50  
```  
  
## <a name="see-also"></a>Voir aussi
 [CHAR &#40;Transact-SQL&#41;](../../t-sql/functions/char-transact-sql.md)  
 [NCHAR &#40;Transact-SQL&#41;](../../t-sql/functions/nchar-transact-sql.md)  
 [UNICODE &#40;Transact-SQL&#41;](../../t-sql/functions/unicode-transact-sql.md)  
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)
  
  


