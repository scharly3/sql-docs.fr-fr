---
title: PDOStatement::bindParam | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0d4dea9ea34f0a2b41db42f641b89ea074139643
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Lie un paramètre à un espace réservé nommé ou de point d’interrogation dans l’instruction SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDOStatement::bindParam($parameter, &$variable[, $data_type[, $length[, $driver_options]]]);  
```  
  
#### <a name="parameters"></a>Paramètres  
$*paramètre*: un identificateur de paramètre (mixte). Pour une instruction à l’aide, des espaces réservés nommés, utilisez un nom de paramètre ( : nom). Pour une instruction préparée à l’aide de la syntaxe de point d’interrogation, il est l’index de base 1 du paramètre.  
  
&$*variable*: le nom (mixte) de la variable PHP à lier au paramètre d’instruction SQL.  
  
$*data_type*: constante PDO::PARAM_ * facultative (entier). Valeur par défaut est PDO::PARAM_STR.  
  
$*longueur*: une longueur (entier) facultatif du type de données. Vous pouvez spécifier PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE pour indiquer la taille par défaut lorsque vous utilisez PDO::PARAM_INT ou PDO::PARAM_BOOL dans $*data_type*.  
  
$*driver_options*: les options spécifiques au pilote de (mixtes) facultatif. Par exemple, vous pouvez spécifier PDO::SQLSRV_ENCODING_UTF8 pour lier la colonne à une variable en tant que chaîne encodée au format UTF-8.  
  
## <a name="return-value"></a>Valeur retournée  
TRUE en cas de réussite ; sinon, FALSE.  
  
## <a name="remarks"></a>Notes  
Lors de la liaison de données de type null pour les colonnes de serveur de type varbinary, binary ou varbinary (max), vous devez spécifier le codage binaire (PDO::SQLSRV_ENCODING_BINARY) à l’aide de la $*driver_options*. Pour plus d’informations sur les constantes d’encodage, consultez [constantes](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

## <a name="example"></a>Exemple  
Cet exemple de code montre qu’après la liaison de $contact au paramètre, le fait de modifier la valeur change la valeur transmise dans la requête.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>Exemple  
Cet exemple de code montre comment accéder à un paramètre de sortie.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(*) from Sys.tables");  
$stmt->bindParam(1, $input1, PDO::PARAM_STR, 10);  
$stmt->execute();  
echo $input1;  
?>  
```  
  
## <a name="example"></a>Exemple  
Cet exemple de code montre comment utiliser un paramètre d’entrée/sortie.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  

> [!NOTE]
> Il est recommandé d’utiliser des chaînes en tant qu’entrées lors de la liaison de valeurs à un [colonne decimal ou numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) pour vérifier la précision et l’exactitude que PHP est limitée à la précision pour [nombres à virgule flottante](http://php.net/manual/en/language.types.float.php).

## <a name="example"></a>Exemple  
Cet exemple de code montre comment lier une valeur décimale en tant que paramètre d’entrée.  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```


## <a name="see-also"></a>Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
