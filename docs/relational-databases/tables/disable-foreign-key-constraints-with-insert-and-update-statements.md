---
title: "Désactiver les contraintes de clé étrangère avec des instructions INSERT et UPDATE | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
- UPDATE statement [SQL Server], foreign key constraints
- INSERT statement [SQL Server], foreign key constraints
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a7f0a16a4a3f1fedb67210e5e4ae096659112cc5
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="disable-foreign-key-constraints-with-insert-and-update-statements"></a>Désactiver les contraintes de clé étrangère avec des instructions INSERT et UPDATE
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Vous pouvez désactiver une contrainte de clé étrangère pendant les transactions INSERT et UPDATE dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Utilisez cette option si vous savez que de nouvelles données violeront la contrainte existante ou si la contrainte s'applique uniquement aux données déjà dans la base de données.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour désactiver une contrainte de clé étrangère pour les instructions INSERT et UPDATE, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Une fois ces contraintes désactivées, les insertions ou les mises à jour ultérieures sur la colonne ne sont pas validées par rapport aux conditions de la contrainte.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a>Pour désactiver une contrainte de clé étrangère avec les instructions INSERT et UPDATE  
  
1.  Dans l' **Explorateur d'objets**, développez la table avec la contrainte, puis développez le dossier **Clés** .  
  
2.  Cliquez avec le bouton droit sur la contrainte et sélectionnez **Modifier**.  
  
3.  Dans la grille sous **Concepteur de tables**, cliquez sur **Appliquer la contrainte de clé étrangère** et sélectionnez **Non** dans le menu déroulant.  
  
4.  Cliquez sur **Fermer**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a>Pour désactiver une contrainte de clé étrangère avec les instructions INSERT et UPDATE  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez les exemples suivants dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
