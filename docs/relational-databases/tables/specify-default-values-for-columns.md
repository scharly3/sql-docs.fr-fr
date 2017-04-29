---
title: "Spécifier des valeurs par défaut pour les colonnes | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 956e23e61cb97d5d1adecf4a06f40f734da42948
ms.lasthandoff: 04/11/2017

---
# <a name="specify-default-values-for-columns"></a>Spécifier des valeurs par défaut pour les colonnes
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Vous pouvez spécifier une valeur par défaut qui sera écrite dans la colonne dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)]. Si vous n'assignez aucune valeur par défaut et que l'utilisateur laisse la colonne vide, alors :  
  
-   Si vous choisissez Oui pour Nul autorisé, la valeur NULL sera insérée dans la colonne.  
  
-   Si vous n'avez pas choisi Oui pour Nul autorisé, la colonne restera vide, mais l'utilisateur ne pourra pas enregistrer la ligne avant d'avoir fourni une valeur pour la colonne.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour spécifier une valeur à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si votre entrée dans le champ **Valeur par défaut** remplace une valeur par défaut liée (qui est affichée sans parenthèses), vous êtes invité à annuler la liaison de la valeur par défaut et à la remplacer par la nouvelle valeur par défaut.  
  
-   Pour entrer une chaîne de texte, placez la valeur entre des guillemets simples (') ; n'utilisez pas de guillemets doubles ("), car ils sont réservés pour les identificateurs entre guillemets.  
  
-   Pour entrer une valeur numérique par défaut, entrez le nombre sans guillemets autour.  
  
-   Pour entrer un objet/une fonction, entrez le nom de l'objet/fonction sans guillemets autour.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>Pour spécifier une valeur par défaut pour une colonne  
  
1.  Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur la table contenant les colonnes dont vous souhaitez modifier l’échelle et cliquez sur **Conception**.  
  
2.  Sélectionnez la colonne pour laquelle vous souhaitez spécifier une valeur par défaut.  
  
3.  Sous l'onglet **Propriétés des colonnes** , entrez la nouvelle valeur par défaut dans la propriété **Valeur ou liaison par défaut** .  
  
    > [!NOTE]  
    >  Pour entrer une valeur par défaut numérique, entrez le nombre. Pour un objet ou une fonction, entrez son nom. Pour une valeur par défaut alphanumérique, entrez la valeur dans des guillemets simples.  
  
4.  Dans le menu **Fichier** , cliquez sur **Enregistrer***nom de la table*.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>Pour spécifier une valeur par défaut pour une colonne  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
    GO  
    INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
    GO  
    ALTER TABLE dbo.doc_exz  
    ADD CONSTRAINT col_b_def  
    DEFAULT 50 FOR column_b ;  
    GO  
  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  