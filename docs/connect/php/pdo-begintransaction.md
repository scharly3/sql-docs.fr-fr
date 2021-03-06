---
title: PDO::beginTransaction | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
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
ms.assetid: 4d5db438-9df7-4d22-9907-3ddc63bd2220
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 51a04874f23dcae77347d85ad0ebd284a1e3b03c
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="pdobegintransaction"></a>PDO::beginTransaction
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Désactive le mode de validation automatique et commence une transaction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDO::beginTransaction();  
```  
  
## <a name="return-value"></a>Valeur retournée  
La valeur est true si l’appel de méthode a réussi, false dans le cas contraire.  
  
## <a name="remarks"></a>Notes  
La transaction commencée avec PDO::beginTransaction termine lorsque [PDO::commit](../../connect/php/pdo-commit.md) ou [PDO::rollback](../../connect/php/pdo-rollback.md) est appelée.  
  
PDO::beginTransaction n’est pas affecté par (et n’affecte pas) la valeur de PDO::ATTR_AUTOCOMMIT.  
  
Vous n’êtes pas autorisé à appeler PDO::beginTransaction avant la fin du précédent PDO::beginTransaction avec PDO::rollback ou PDO::commit.  
  
La connexion revient au mode de validation automatique si cette méthode échoue.  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
L’exemple suivant utilise une base de données nommée Test et une table nommée Table1. Il démarre une transaction, émet des commandes pour ajouter deux lignes, puis supprime une ligne. Les commandes sont envoyées à la base de données et la transaction est explicitement terminée par `PDO::commit`.  
  
```  
<?php  
   $conn = new PDO( "sqlsrv:server=(local); Database = Test", "", "");  
   $conn->beginTransaction();  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'b') ");  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'c') ");  
   $ret = $conn->exec("delete from Table1 where col1 = 'a' and col2 = 'b'");  
   $conn->commit();  
   // $conn->rollback();  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
