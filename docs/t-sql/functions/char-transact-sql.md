---
title: CHAR (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
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
- char_TSQL
- char
dev_langs:
- TSQL
helpviewer_keywords:
- converting int ACSII code to character
- control characters
- tab
- ASCII conversions
- CHAR function
- carriage return
- inserting control characters
- characters [SQL Server], control
- line feed
- printing ASCII values
ms.assetid: 955afe94-539c-465d-af22-16ec45da432a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5dd3a4f8b6fd308560ddcf2db3c6940625dc6ee3
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="char-transact-sql"></a>CHAR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Convertit un code ASCII **int** en un caractère.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CHAR ( integer_expression )  
```  
  
## <a name="arguments"></a>Arguments  
*integer_expression*  
Entier compris entre 0 et 255. `NULL` est renvoyé si l’expression entière ne se situe pas dans cette plage.
  
## <a name="return-types"></a>Types de retour
**char(1)**
  
## <a name="remarks"></a>Notes   
`CHAR` permet également d’insérer des caractères de contrôle dans des chaînes de caractères. Le tableau suivant répertorie quelques-uns des caractères de contrôle les plus utilisés.
  
|Caractère de contrôle|Valeur|  
|---|---|
|Onglet|**char(9)**|  
|Saut de ligne|**char(10)**|  
|Retour chariot|**char(13)**|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-ascii-and-char-to-print-ascii-values-from-a-string"></a>A. Utilisation d'ASCII et CHAR pour imprimer les valeurs ASCII d'une chaîne  
L'exemple suivant imprime la valeur et le caractère ASCII de chacun des caractères de la chaîne `New Moon`.
  
```sql
SET TEXTSIZE 0;  
-- Create variables for the character string and for the current   
-- position in the string.  
DECLARE @position int, @string char(8);  
-- Initialize the current position and the string variables.  
SET @position = 1;  
SET @string = 'New Moon';  
WHILE @position <= DATALENGTH(@string)  
   BEGIN  
   SELECT ASCII(SUBSTRING(@string, @position, 1)),   
      CHAR(ASCII(SUBSTRING(@string, @position, 1)))  
   SET @position = @position + 1  
   END;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------- -
78          N  
----------- -  
101         e  
----------- -  
119         w  
----------- -  
32  
----------- -  
77          M  
----------- -  
111         o  
----------- -  
111         o  
----------- - 
110         n  
```
  
### <a name="b-using-char-to-insert-a-control-character"></a>B. Utilisation de CHAR pour l'insertion d'un caractère de contrôle  
L'exemple suivant utilise `CHAR(13)` pour imprimer le nom et l'adresse de messagerie d'un employé sur des lignes distinctes, lorsque les résultats sont retournés sous forme de texte. Cet exemple utilise la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
SELECT p.FirstName + ' ' + p.LastName, + CHAR(13)  + pe.EmailAddress   
FROM Person.Person p JOIN Person.EmailAddress pe  
ON p.BusinessEntityID = pe.BusinessEntityID  
AND p.BusinessEntityID = 1;  
GO  
```
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Ken Sanchez
ken0@adventure-works.com
  
(1 row(s) affected)
```
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-ascii-and-char-to-print-ascii-values-from-a-string"></a>C. Utilisation d'ASCII et CHAR pour imprimer les valeurs ASCII d'une chaîne  
L’exemple suivant suppose un jeu de caractères ASCII et renvoie la valeur de caractère pour 6 nombres de caractère ASCII.
  
```sql
SELECT CHAR(65) AS [65], CHAR(66) AS [66],   
CHAR(97) AS [97], CHAR(98) AS [98],   
CHAR(49) AS [49], CHAR(50) AS [50];  
```
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
65   66   97   98   49   50  
---- ---- ---- ---- ---- ----  
A    B    a    b    1    2  
```
  
### <a name="d-using-char-to-insert-a-control-character"></a>D. Utilisation de CHAR pour l'insertion d'un caractère de contrôle  
L’exemple suivant utilise `CHAR(13)` pour renvoyer des informations sur les bases de données sur des lignes distinctes, lorsque les résultats sont renvoyés sous forme de texte.
  
```sql
SELECT name, 'was created on ', create_date, CHAR(13), name, 'is currently ', state_desc   
FROM sys.databases;  
GO  
```
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
name     create_date    name    state_desc  
------------------------------------------------------------  
master                   was created on  2003-04-08 09:13:36.390   
master                   is currently  ONLINE  
tempdb                   was created on  2014-01-10 17:24:24.023   
tempdb                   is currently  ONLINE  
AdventureWorksPDW2012    was created on  2014-05-07 09:05:07.083 
AdventureWorksPDW2012    is currently  ONLINE  
```
  
## <a name="see-also"></a>Voir aussi
 [ASCII &#40;Transact-SQL&#41;](../../t-sql/functions/ascii-transact-sql.md)  
 [NCHAR &#40;Transact-SQL&#41;](../../t-sql/functions/nchar-transact-sql.md)  
 [UNICODE &#40;Transact-SQL&#41;](../../t-sql/functions/unicode-transact-sql.md)  
 [+ &#40;Concaténation de chaînes&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)
  
  

