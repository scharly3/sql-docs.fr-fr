---
title: "Suppression des objets de base de données | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d8e3d5eba52076ae58337fb9579781cad10a5f42
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-3-1---deleting-database-objects"></a>Leçon 3-1 - Suppression des objets de base de données
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)] Pour supprimer toutes les traces de ce tutoriel, supprimez simplement la base de données. Cependant, dans cette rubrique, vous allez parcourir les étapes pour inverser chaque action effectuée au cours du tutoriel.  
  
### <a name="removing-permissions-and-objects"></a>Suppression des autorisations et des objets  
  
1.  Avant de supprimer des objets, vérifiez que vous êtes dans la bonne base de données :  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  Utilisez l'instruction `REVOKE` pour supprimer une autorisation d'exécution pour `Mary` sur la procédure stockée :  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  Utilisez l'instruction `DROP` pour supprimer une autorisation pour `Mary` d'accéder à la base de données `TestData` :  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  Utilisez l'instruction `DROP` pour supprimer une autorisation pour `Mary` d'accéder à cette instance de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  Utilisez l'instruction `DROP` pour supprimer la procédure stockée `pr_Names`:  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  Utilisez l'instruction `DROP` pour supprimer la vue `vw_Names`:  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  Utilisez l'instruction `DELETE` pour supprimer toutes les lignes de la table `Products` :  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  Utilisez l'instruction `DROP` pour supprimer la table `Products` :  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. Vous ne pouvez pas supprimer la base de données `TestData` lorsque vous êtes dans celle-ci ; par conséquent, basculez d'abord le contexte vers une autre base de données, puis utilisez l'instruction `DROP` pour supprimer la base de données `TestData` :  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
Cette étape conclut le tutoriel d'écriture d'instructions [!INCLUDE[tsql](../includes/tsql-md.md)] . N'oubliez pas que ce tutoriel est une brève présentation et ne décrit pas toutes les options des instructions utilisées. La conception et la création d'une structure de base de données efficace et la configuration de l'accès sécurisé aux données nécessitent une base de données plus complexe que celle de ce tutoriel.  
  
## <a name="return-to-sql-server-tools-portal"></a>Revenir au portail des outils SQL Server  
[Tutoriel : écriture d'instructions Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a> Voir aussi  
[REVOKE &#40;Transact-SQL&#41;](../t-sql/statements/revoke-transact-sql.md)  
[DROP USER &#40;Transact-SQL&#41;](../t-sql/statements/drop-user-transact-sql.md)  
[DROP LOGIN &#40;Transact-SQL&#41;](../t-sql/statements/drop-login-transact-sql.md)  
[DROP PROCEDURE &#40;Transact-SQL&#41;](../t-sql/statements/drop-procedure-transact-sql.md)  
[DROP VIEW &#40;Transact-SQL&#41;](../t-sql/statements/drop-view-transact-sql.md)  
[DELETE &#40;Transact-SQL&#41;](../t-sql/statements/delete-transact-sql.md)  
[DROP TABLE &#40;Transact-SQL&#41;](../t-sql/statements/drop-table-transact-sql.md)  
[DROP DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/drop-database-transact-sql.md)  
  
  
  
