---
title: "Param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-non-specified"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "procédures stockées [SQL Server], paramètres"
  - "fonctions définies par l’utilisateur [SQL Server], paramètres"
ms.assetid: c1f9bd93-3271-4098-a23b-7bd7a19ab65b
caps.latest.revision: 2
author: "pmasl"
ms.author: "pelopes"
manager: "jhubbard"
caps.handback.revision: 2
---
# Param&#232;tres
Les paramètres sont utilisés pour échanger des données entre d'une part une procédure stockée ou une fonction et d'autre part, l'application ou l'outil ayant appelé la procédure stockée ou la fonction : 

*  Les paramètres d'entrée permettent à l'appelant de faire passer une valeur de donnée à la procédure stockée ou à la fonction.
*  Les paramètres de sortie permettent à la procédure stockée de faire passer en retour une valeur de donnée à l'appelant. Les fonctions définies par l'utilisateur ne peuvent pas définir de paramètres de sortie.
*  Chaque procédure stockée renvoie un code de retour de type entier à l'appelant. Si la procédure stockée ne définit pas explicitement la valeur du code de retour, la valeur de ce code est 0.

La procédure stockée suivante utilise un paramètre d'entrée, un paramètre de sortie et un code de retour :
```
-- Create a procedure that takes one input parameter and returns one output parameter and a return code.
CREATE PROCEDURE SampleProcedure @EmployeeIDParm INT,
         @MaxTotal INT OUTPUT
AS
-- Declare and initialize a variable to hold @@ERROR.
DECLARE @ErrorSave INT
SET @ErrorSave = 0

-- Do a SELECT using the input parameter.
SELECT FirstName, LastName, JobTitle
FROM HumanResources.vEmployee
WHERE EmployeeID = @EmployeeIDParm

-- Save any nonzero @@ERROR value.
IF (@@ERROR <> 0)
   SET @ErrorSave = @@ERROR

-- Set a value in the output parameter.
SELECT @MaxTotal = MAX(TotalDue)
FROM Sales.SalesOrderHeader;

IF (@@ERROR <> 0)
   SET @ErrorSave = @@ERROR

-- Returns 0 if neither SELECT statement had an error; otherwise, returns the last error.
RETURN @ErrorSave
GO
```

Lorsqu'une procédure stockée ou une fonction est exécutée, les paramètres d'entrée peuvent avoir une valeur constante ou variable. Les paramètres de sortie et les codes de retour doivent renvoyer leur valeur dans une variable. Les paramètres et les codes de retour peuvent échanger des valeurs de données avec les variables Transact-SQL ou des variables d’application.

Si une procédure stockée est appelée par un traitement ou un script, les valeurs des paramètres et du code de retour peuvent utiliser des variables Transact-SQL définies dans le même traitement. L'exemple suivant présente un traitement qui exécute la procédure créée précédemment. Le paramètre d’entrée est spécifié comme constante tandis que le paramètre de sortie et le code de retour ont pour valeur des variables Transact-SQL :
```
-- Declare the variables for the return code and output parameter.
DECLARE @ReturnCode INT
DECLARE @MaxTotalVariable INT

-- Execute the stored procedure and specify which variables
-- are to receive the output parameter and return code values.
EXEC @ReturnCode = SampleProcedure @EmployeeIDParm = 19,
   @MaxTotal = @MaxTotalVariable OUTPUT

-- Show the values returned.
PRINT ' '
PRINT 'Return code = ' + CAST(@ReturnCode AS CHAR(10))
PRINT 'Maximum Quantity = ' + CAST(@MaxTotalVariable AS CHAR(10))
GO
```

Une application peut utiliser des marqueurs de paramètres liés à des variables de programme pour échanger des données entre des variables d'application, des paramètres et des codes de retour.

## <a name="see-also"></a>Voir aussi
[CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)   
 [Section Réutilisation des paramètres et des plans d’exécution](../../relational-databases/query-processing-architecture-guide.md)   
 [Variables (Transact-SQL)](../../t-sql/language-elements/variables-transact-sql.md)