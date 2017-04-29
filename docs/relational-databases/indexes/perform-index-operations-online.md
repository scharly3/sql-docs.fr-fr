---
title: "Ex&#233;cuter des op&#233;rations en ligne sur les index | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "opérations en ligne sur les index [SQL Server]"
  - "opérations en ligne sur l'index"
  - "ONLINE (option)"
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Ex&#233;cuter des op&#233;rations en ligne sur les index
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cette rubrique explique comment créer, reconstruire ou supprimer des index en ligne dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option ONLINE permet l'accès simultané des utilisateurs aux tables sous-jacentes ou aux données des index cluster et aux index non-cluster associés pendant ces opérations sur les index. Par exemple, pendant qu'un index cluster est reconstruit par un utilisateur, cet utilisateur et d'autres peuvent continuer de mettre à jour et d'interroger les données sous-jacentes. Lorsque vous effectuez des opérations DDL (Data Definition Language) en mode hors connexion, comme la construction ou la reconstruction d'un index cluster, ces opérations posent des verrous exclusifs sur les données sous-jacentes et les index associés. Ces verrous empêchent toute modification et toute interrogation des données sous-jacentes jusqu'à la fin de l'opération effectuée sur l'index.  
  
> [!NOTE]  
>  Les opérations d'index en ligne ne sont pas disponibles dans toutes les édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour reconstruire un index en ligne à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Il est recommandé d'effectuer les opérations sur les index en ligne dans les environnements qui sont opérationnels 24 heures sur 24 et 7 jours sur 7, dans lesquels il est vital de maintenir l'accès des utilisateurs.  
  
-   L'option ONLINE peut être utilisée dans les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes.  
  
    -   [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)  
  
    -   [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)  
  
    -   [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md)  
  
    -   [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) (Pour ajouter ou supprimer des contraintes UNIQUE ou PRIMARY KEY avec l’option d’index CLUSTERED)  
  
-   Pour plus d’informations sur les limitations et les restrictions de création, reconstruction ou suppression d’index en ligne, consultez [Instructions pour les opérations d’index en ligne](../../relational-databases/indexes/guidelines-for-online-index-operations.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite une autorisation ALTER sur la table ou la vue.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour reconstruire un index en ligne  
  
1.  Dans l'Explorateur d'objets, cliquez sur le signe plus (+) pour développer la base de données qui contient la table sur laquelle vous souhaitez reconstruire un index en ligne.  
  
2.  Développez le dossier **Tables** .  
  
3.  Cliquez sur le signe plus (+) pour développer la table sur laquelle vous souhaitez reconstruire un index en ligne.  
  
4.  Développez le dossier **Index** .  
  
5.  Cliquez avec le bouton droit sur l’index à reconstruire en ligne, puis sélectionnez **Propriétés**.  
  
6.  Sous **Sélectionner une page**, sélectionnez **Options**.  
  
7.  Sélectionnez **Autoriser le traitement des instructions DML en ligne**, puis sélectionnez **True** dans la liste.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez avec le bouton droit sur l’index à reconstruire en ligne, puis sélectionnez **Reconstruire**.  
  
10. Dans la boîte de dialogue **Reconstruire les index** , vérifiez que l'index correct figure dans la grille **Index à reconstruire** , puis cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour créer, reconstruire ou supprimer un index en ligne  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple reconstruit un index en ligne existant.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     L'exemple suivant supprime un index cluster en ligne et déplace la table résultante (segment de mémoire) vers le groupe de fichiers `NewGroup` en utilisant la clause `MOVE TO`. Les affichages catalogue `sys.indexes`, `sys.tables`et `sys.filegroups` sont interrogés pour vérifier le placement de l'index et de la table dans les groupes de fichiers avant et après l'opération de déplacement.  
  
     [!code-sql[IndexDDL#DropIndex4](../../relational-databases/indexes/codesnippet/tsql/perform-index-operations_1.sql)]  
  
 Pour plus d’informations, consultez [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
  