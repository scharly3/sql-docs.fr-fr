---
title: "Afficher une liste des bases de donn&#233;es sur une instance de SQL&#160;Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bases de données actuelles"
  - "bases de données actuellement sur le serveur [SQL Server]"
  - "liste de base de données [SQL Server]"
  - "affichage de la liste de base de données"
  - "affichage de la liste de base de données"
  - "bases de données [SQL Server], affichage"
  - "serveurs [SQL Server], bases de données répertoriées sur"
  - "répertorier les bases de données"
ms.assetid: 7ee7a789-db36-4be9-8a0e-0362a1e152dd
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Afficher une liste des bases de donn&#233;es sur une instance de SQL&#160;Server
  Cette rubrique explique comment afficher une liste des bases de données sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher une liste des bases de données sur une instance de SQL Server, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Si l’appelant de **sys.databases** n’est pas le propriétaire de la base de données et si celle-ci n’est pas de type **master** ou **tempdb**, les autorisations minimales requises pour consulter la ligne correspondante sont les autorisations ALTER ANY DATABASE ou VIEW ANY DATABASE au niveau du serveur, ou encore l’autorisation CREATE DATABASE dans la base de données **master**. La base de données à laquelle l'appelant est connecté peut toujours être vue dans **sys.databases**.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour afficher une liste des bases de données sur une instance de SQL Server  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], puis développez-la.  
  
2.  Pour afficher une liste de toutes les bases de données de l'instance, développez **Bases de données**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour afficher une liste des bases de données sur une instance de SQL Server  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple retourne une liste des bases de données de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La liste inclut les noms des bases de données, leurs ID de base de données, et les dates auxquelles les bases de données ont été créées.  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT name, database_id, create_date  
FROM sys.databases ;  
GO  
  
```  
  
## Voir aussi  
 [Affichages catalogue de bases de données et de fichiers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  