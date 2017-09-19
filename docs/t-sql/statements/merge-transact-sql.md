---
title: FUSION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MERGE
- MERGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- updating data [SQL Server]
- modifying data [SQL Server], MERGE statement
- MERGE statement [SQL Server]
- adding data
- DML [SQL Server], MERGE statement
- table modifications [SQL Server], MERGE statement
- data manipulation language [SQL Server], MERGE statement
- inserting data
ms.assetid: c17996d6-56a6-482f-80d8-086a3423eecc
caps.latest.revision: 76
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d071a0137d39abb638131df391c72eae75292c08
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="merge-transact-sql"></a>MERGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Effectue des opérations d'insertion, de mise à jour ou de suppression sur une table cible selon les résultats d'une jointure avec une table source. Par exemple, vous pouvez synchroniser deux tables en insérant, mettant à jour ou supprimant des lignes dans une seule table selon les différences trouvées dans l'autre table.  
  
 **Conseil de performances :** le comportement conditionnel décrit pour l’instruction MERGE fonctionne mieux lorsque les deux tables ont un mélange complexe de caractéristiques correspondantes. Par exemple, l'insertion d'une ligne si elle n'existe pas ou la mise à jour de la ligne si elle correspond. Vous pouvez améliorer les performances et l'extensibilité lors d'une simple mise à jour d'une table basée sur les lignes d'une autre table en utilisant les instructions INSERT, UPDATE et DELETE. Exemple :  
  
```  
INSERT tbl_A (col, col2)  
SELECT col, col2   
FROM tbl_B   
WHERE NOT EXISTS (SELECT col FROM tbl_A A2 WHERE A2.col = tbl_B.col);  
```  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ WITH <common_table_expression> [,...n] ]  
MERGE   
    [ TOP ( expression ) [ PERCENT ] ]   
    [ INTO ] <target_table> [ WITH ( <merge_hint> ) ] [ [ AS ] table_alias ]  
    USING <table_source>   
    ON <merge_search_condition>  
    [ WHEN MATCHED [ AND <clause_search_condition> ]  
        THEN <merge_matched> ] [ ...n ]  
    [ WHEN NOT MATCHED [ BY TARGET ] [ AND <clause_search_condition> ]  
        THEN <merge_not_matched> ]  
    [ WHEN NOT MATCHED BY SOURCE [ AND <clause_search_condition> ]  
        THEN <merge_matched> ] [ ...n ]  
    [ <output_clause> ]  
    [ OPTION ( <query_hint> [ ,...n ] ) ]      
;  
  
<target_table> ::=  
{   
    [ database_name . schema_name . | schema_name . ]  
  target_table  
}  
  
<merge_hint>::=  
{  
    { [ <table_hint_limited> [ ,...n ] ]  
    [ [ , ] INDEX ( index_val [ ,...n ] ) ] }  
}  
  
<table_source> ::=   
{  
    table_or_view_name [ [ AS ] table_alias ] [ <tablesample_clause> ]   
        [ WITH ( table_hint [ [ , ]...n ] ) ]   
  | rowset_function [ [ AS ] table_alias ]   
        [ ( bulk_column_alias [ ,...n ] ) ]   
  | user_defined_function [ [ AS ] table_alias ]  
  | OPENXML <openxml_clause>   
  | derived_table [ AS ] table_alias [ ( column_alias [ ,...n ] ) ]   
  | <joined_table>   
  | <pivoted_table>   
  | <unpivoted_table>   
}  
  
<merge_search_condition> ::=  
    <search_condition>  
  
<merge_matched>::=  
    { UPDATE SET <set_clause> | DELETE }  
  
<set_clause>::=  
SET  
  { column_name = { expression | DEFAULT | NULL }  
  | { udt_column_name.{ { property_name = expression  
                        | field_name = expression }  
                        | method_name ( argument [ ,...n ] ) }  
    }  
  | column_name { .WRITE ( expression , @Offset , @Length ) }  
  | @variable = expression  
  | @variable = column = expression  
  | column_name { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  | @variable { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  | @variable = column { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  } [ ,...n ]   
  
<merge_not_matched>::=  
{  
    INSERT [ ( column_list ) ]   
        { VALUES ( values_list )  
        | DEFAULT VALUES }  
}  
  
<clause_search_condition> ::=  
    <search_condition>  
  
<search condition> ::=  
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | ! > | < | < = | ! < } expression   
    | string_expression [ NOT ] LIKE string_expression   
  [ ESCAPE 'escape_character' ]   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | CONTAINS   
  ( { column | * } , '< contains_search_condition >' )   
    | FREETEXT ( { column | * } , 'freetext_string' )   
    | expression [ NOT ] IN ( subquery | expression [ ,...n ] )   
    | expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
  { ALL | SOME | ANY} ( subquery )   
    | EXISTS ( subquery ) }   
  
<output_clause>::=  
{  
    [ OUTPUT <dml_select_list> INTO { @table_variable | output_table }  
        [ (column_list) ] ]  
    [ OUTPUT <dml_select_list> ]  
}  
  
<dml_select_list>::=  
    { <column_name> | scalar_expression }   
        [ [AS] column_alias_identifier ] [ ,...n ]  
  
<column_name> ::=  
    { DELETED | INSERTED | from_table_name } . { * | column_name }  
    | $action  
```  
  
## <a name="arguments"></a>Arguments  
 AVEC \<common_table_expression >  
 Spécifie le jeu de résultats ou la vue nommés temporaires, également appelés expression de table commune et définis dans le cadre de l'instruction MERGE. Le jeu de résultats est dérivé d'une simple requête et est référencé par l'instruction MERGE. Pour plus d’informations, consultez [avec common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 HAUT ( *expression* ) [%]  
 Spécifie le nombre ou le pourcentage de lignes affectées. *expression* peut être un nombre ou un pourcentage de lignes. Les lignes référencées dans l'expression TOP ne sont pas triées dans un ordre donné. Pour plus d’informations, consultez [TOP &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 La clause TOP est appliquée après la jointure de l'intégralité de la table source et de la table cible, et après la suppression des lignes jointes qui ne sont pas éligibles pour une opération de type INSERT, UPDATE ou DELETE. La clause TOP réduit le nombre de lignes jointes à la valeur spécifiée et les actions INSERT, UPDATE ou DELETE sont appliquées aux lignes jointes restantes sans respecter un ordre particulier. Les lignes ne sont donc pas réparties selon un ordre particulier dans le cadre des actions définies dans les clauses WHEN. Par exemple, la spécification de la clause TOP (10) affecte 10 lignes, dont 7 peuvent être mises à jour et 3 insérées, ou alors 1 ligne peut être supprimée, 5 mises à jour et 4 insérées, et ainsi de suite.  
  
 Étant donné que l'instruction MERGE effectue une analyse complète des tables source et cible, les performances d'E/S peuvent être affectées lorsque la clause TOP est utilisée pour modifier une table volumineuse en créant plusieurs lots. Dans ce scénario, il est important de s'assurer que tous les lots consécutifs ciblent les nouvelles lignes.  
  
 *database_name*  
 Nom de la base de données dans laquelle *table_cible* se trouve.  
  
 *schema_name*  
 Est le nom du schéma auquel *table_cible* appartient.  
  
 *table_cible*  
 Table ou vue sur laquelle les données des lignes de \<table_source > sont mis en correspondance en fonction de \<clause_search_condition >. *table_cible* est la cible de toute instruction insert, update ou les opérations de suppression spécifiées par les clauses WHEN de l’instruction MERGE.  
  
 Si *table_cible* est une vue, toutes les opérations dont il doivent satisfaire les conditions de mise à jour des vues. Pour plus d’informations, consultez [modifier les données via une vue](../../relational-databases/views/modify-data-through-a-view.md).  
  
 *table_cible* ne peut pas être une table distante. *table_cible* ne peut pas avoir de règles définies sur elle.  
  
 [EN] *alias_de_table*  
 Autre nom utilisé pour faire référence à une table.  
  
 À l’aide de \<table_source >  
 Spécifie la source de données qui est mis en correspondance avec les lignes de données dans *table_cible* selon \<merge_search condition >. Le résultat de cette correspondance dicte les actions à effectuer par les clauses WHEN de l'instruction MERGE. \<table_source > peut être une table distante ou une table dérivée qui accède aux tables distantes. 
  
 \<table_source > peut être une table dérivée qui utilise le [!INCLUDE[tsql](../../includes/tsql-md.md)] [constructeur de valeurs de table](../../t-sql/queries/table-value-constructor-transact-sql.md) pour construire une table en spécifiant plusieurs lignes.  
  
 Pour plus d’informations sur la syntaxe et les arguments de cette clause, consultez [FROM &#40; Transact-SQL &#41; ](../../t-sql/queries/from-transact-sql.md).  
  
 ON \<merge_search_condition >  
 Spécifie les conditions sur lequel \<table_source > est jointe à *table_cible* pour déterminer où la correspondance. 
  
> [!CAUTION]  
>  Il est important de spécifier uniquement les colonnes de la table cible utilisées à des fins de correspondance. Autrement dit, spécifiez les colonnes de la table cible qui seront comparées à la colonne correspondante de la table source. N'essayez pas d'améliorer les performances des requêtes en éliminant par filtrage des lignes de la table cible dans la clause ON, via la spécification de `AND NOT target_table.column_x = value`, par exemple. Cette approche peut retourner des résultats inattendus et incorrects.  
  
 En cas de correspondance puis \<merge_matched >  
 Spécifie que toutes les lignes de *table_cible* qui correspondent aux lignes retournées par \<table_source > ON \<merge_search_condition > et répondent aux critères de recherche supplémentaires, sont mis à jour ou supprimées en fonction de la \<merge_matched > clause.  
  
 L'instruction MERGE peut avoir au plus deux clauses WHEN MATCHED. Si deux clauses sont spécifiées, la première clause doit être accompagnée d’un AND \<search_condition > clause. Pour toute ligne donnée, la deuxième clause WHEN MATCHED est appliquée uniquement si la première ne l'est pas. En présence de deux clauses WHEN MATCHED, l'une d'elles doit spécifier une action UPDATE et l'autre une action DELETE. Si la mise à jour est spécifié dans le \<merge_matched > clause et plusieurs lignes de \<table_source > correspond à une ligne dans *table_cible* selon \<merge_search_condition >, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renvoie une erreur. L'instruction MERGE ne peut pas mettre à jour la même ligne plus d'une fois, ou mettre à jour et supprimer la même ligne.  
  
 WHEN NOT MATCHED [BY TARGET] puis \<merge_not_matched >  
 Spécifie qu’une ligne est insérée dans *table_cible* pour chaque ligne retournée par \<table_source > ON \<merge_search_condition > qui ne correspond pas à une ligne dans *table_cible*, mais satisfait à une condition de recherche supplémentaire, le cas échéant. Les valeurs à insérer sont spécifiées par le \<merge_not_matched > clause. L'instruction MERGE peut avoir une seule clause WHEN NOT MATCHED.  
  
 Lorsque NOT MATCHED BY SOURCE puis \<merge_matched >  
 Spécifie que toutes les lignes de *table_cible* qui ne correspondent pas les lignes retournées par \<table_source > ON \<merge_search_condition >, et qui répondent aux critères de recherche supplémentaires, sont mis à jour ou supprimées en fonction de la \<merge_matched > clause.  
  
 L'instruction MERGE peut avoir au plus deux clauses WHEN NOT MATCHED BY SOURCE. Si deux clauses sont spécifiées, la première clause doit être accompagnée d’un AND \<clause_search_condition > clause. Pour toute ligne donnée, la deuxième clause WHEN NOT MATCHED BY SOURCE est appliquée uniquement si la première ne l'est pas. En présence de deux clauses WHEN NOT MATCHED BY SOURCE, l'une d'elles doit spécifier une action UPDATE et l'autre une action DELETE. Seules les colonnes de la table cible peuvent être référencées dans \<clause_search_condition >.  
  
 Lorsqu’aucune ligne n’est retournée par \<table_source >, les colonnes de la table source n’est pas accessible. Si l’action update ou delete spécifiée dans le \<merge_matched > clause fait référence à des colonnes dans la table source, l’erreur 207 (nom de colonne non valide) est retournée. Par exemple, la clause `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` peut faire en sorte que l'instruction échoue dans la mesure où `Col1` dans la table source est inaccessible.  
  
 ET \<clause_search_condition >  
 Spécifie toute condition de recherche valide. Pour plus d’informations, consultez [Condition de recherche &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
 \<table_hint_limited >  
 Spécifie un ou plusieurs indicateurs de table qui sont appliqués à la table cible pour chaque opération INSERT, UPDATE ou DELETE exécutée par l'instruction MERGE. Le mot clé WITH et les parenthèses sont obligatoires.  
  
 NOLOCK et READUNCOMMITTED ne sont pas autorisés. Pour plus d’informations sur les indicateurs de table, consultez [indicateurs de Table &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
 La spécification de l'indicateur TABLOCK sur une table qui est la cible d'une instruction INSERT a le même effet que la spécification de l'indicateur TABLOCKX. Un verrou exclusif est appliqué à la table. Lorsque FORCESEEK est spécifié, il s'applique à l'instance implicite de la table cible jointe à la table source.  
  
> [!CAUTION]  
>  Le fait de spécifier READPAST avec WHEN NOT MATCHED [ BY TARGET ] THEN INSERT peut se traduire par des opérations INSERT qui violent des contraintes UNIQUE.  
  
 INDEX ( index_val [ ,...n ] )  
 Spécifie le nom ou l'ID d'un ou de plusieurs index sur la table cible pour effectuer une jointure implicite avec la table source. Pour plus d’informations, consultez [Indicateurs de table &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md).  
  
 \<output_clause >  
 Retourne une ligne pour chaque ligne de *table_cible* qui est mis à jour, insérée ou supprimée dans aucun ordre particulier. **$action** peut être spécifié dans la clause output. **$action** est une colonne de type **nvarchar (10)** qui retourne l’une des trois valeurs pour chaque ligne : 'INSERT', 'UPDATE' ou 'DELETE', en fonction de l’action qui a été effectuée sur cette ligne. Pour plus d’informations sur les arguments de cette clause, consultez [Clause OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
 OPTION ( \<query_hint > [,.. .n])  
 Spécifie que des indicateurs de l'optimiseur sont utilisés pour personnaliser la façon dont le moteur de base de données traite l'instruction. Pour plus d’informations, consultez [Indicateurs de requête &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md).  
  
 \<merge_matched >  
 Spécifie la mise à jour ou supprimer l’action qui est appliquée à toutes les lignes de *table_cible* qui ne correspondent pas les lignes retournées par \<table_source > ON \<merge_search_condition >, et qui répondent aux critères de recherche supplémentaires.  
  
 Mise à jour \<set_clause >  
 Spécifie la liste de noms de colonne ou de variable à mettre à jour dans la table cible et les valeurs avec lesquelles les mettre à jour.  
  
 Pour plus d’informations sur les arguments de cette clause, consultez [mise à jour &#40; Transact-SQL &#41; ](../../t-sql/queries/update-transact-sql.md). La définition d'une variable à la même valeur qu'une colonne n'est pas autorisée.  
  
 DELETE  
 Spécifie que les lignes qui correspondent aux lignes dans *table_cible* sont supprimés.  
  
 \<merge_not_matched >  
 Spécifie les valeurs à insérer dans la table cible.  
  
 (*column_list*)  
 Liste d'une ou de plusieurs colonnes de la table cible dans lesquelles insérer des données. Les colonnes doivent être spécifiées comme un nom en une seule partie sinon l'instruction MERGE échouera. *column_list* doit être placée entre parenthèses et délimitée par des virgules.  
  
 VALEURS ( *liste_de_valeurs*)  
 Liste séparée par des virgules et contenant des constantes, variables ou expressions qui retourne les valeurs à insérer dans la table cible. Les expressions ne peuvent pas contenir d'instruction EXECUTE.  
  
 DEFAULT VALUES  
 Force la ligne insérée à prendre les valeurs par défaut définies pour chaque colonne.  
  
 Pour plus d’informations sur cette clause, consultez [INSERT &#40; Transact-SQL &#41; ](../../t-sql/statements/insert-transact-sql.md).  
  
 \<condition de recherche >  
 Spécifie les conditions de recherche permet de spécifier \<merge_search_condition > ou \<clause_search_condition >. Pour plus d’informations sur les arguments pour cette clause, consultez [Condition de recherche &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
## <a name="remarks"></a>Notes  
 Au moins l'une des trois clauses MATCHED doit être spécifiée, mais cela peut être dans n'importe quel ordre. Une variable ne peut pas être mise à jour plus d'une fois dans la même clause MATCHED.  
  
 Toute opération d'insertion, de mise à jour ou de suppression spécifiée sur la table cible par l'instruction MERGE est limitée par toutes contraintes qui s'appliquent à elle, notamment les contraintes d'intégrité référentielle en cascade. Si IGNORE_DUP_KEY a la valeur ON pour un index unique sur la table cible, MERGE ignore ce paramètre.  
  
 L'instruction MERGE requiert un point-virgule (;) comme terminateur d'instruction. L'erreur 10713 est générée lorsqu'une instruction MERGE est exécutée sans le terminateur.  
  
 Lorsqu’il est utilisé après la fusion, [@@ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/functions/rowcount-transact-sql.md) retourne le nombre total de lignes insérées, mises à jour et supprimés au client.  
  
 MERGE est un mot clé entièrement réservé lorsque le niveau de compatibilité de la base de données a la valeur 100 ou une valeur supérieure. L'instruction MERGE est disponible sous les niveaux de compatibilité de base de données 90 et 100 ; cependant, le mot clé n'est pas entièrement réservé lorsque le niveau de compatibilité de la base de données a la valeur 90.  
  
 Le **fusion** instruction ne doit pas être utilisée lors de la réplication avec mise à jour la file d’attente à l’aide. Le **fusion** et le déclencheur de mise à jour en file d’attente ne sont pas compatibles. Remplacez le **fusion** instruction avec une instruction insert ou une mise à jour.  
  
## <a name="trigger-implementation"></a>Implémentation de déclencheur  
 Pour chaque opération INSERT, UPDATE ou DELETE spécifiée dans l'instruction MERGE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lance tous les déclencheurs AFTER correspondants définis sur la table cible, mais ne garantit pas l'opération sur laquelle les déclencheurs seront lancés en premier ou en dernier. Les déclencheurs définis pour la même opération respectent l'ordre que vous spécifiez. Pour plus d’informations sur la définition d’ordre de lancement des déclencheurs, consultez [spécifier le premier et dernier déclencheurs](../../relational-databases/triggers/specify-first-and-last-triggers.md).  
  
 Si la table cible a un déclencheur INSTEAD OF actif défini pour une opération INSERT, UPDATE ou DELETE effectuée par une instruction MERGE, elle doit avoir un déclencheur INSTEAD OF actif pour toutes les opérations spécifiées dans l'instruction MERGE.  
  
 N’importe quel INSTEAD OF UPDATE ou si les déclencheurs INSTEAD OF DELETE définis sur *table_cible*, les opérations update ou delete ne sont pas effectuées. Au lieu de cela, les déclencheurs sont lancés et **inséré** et **supprimé** les tables sont remplies en conséquence.  
  
 S’il y en a au lieu de déclencheurs d’insertion définis sur *table_cible*, l’opération d’insertion n’est pas effectuée. Au lieu de cela, les déclencheurs sont lancés et **inséré** table est remplie en conséquence.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation SELECT sur la table source et les autorisations INSERT, UPDATE ou DELETE sur la table cible. Pour plus d’informations, consultez la section autorisations dans le [sélectionnez](../../t-sql/queries/select-transact-sql.md), [insérer](../../t-sql/statements/insert-transact-sql.md), [mise à jour](../../t-sql/queries/update-transact-sql.md), et [supprimer](../../t-sql/statements/delete-transact-sql.md) rubriques.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-merge-to-perform-insert-and-update-operations-on-a-table-in-a-single-statement"></a>A. Utilisation de MERGE pour effectuer des opérations INSERT et UPDATE sur une table dans une instruction unique  
 L'un des scénarios classiques consiste à mettre à jour une ou plusieurs colonnes dans une table si une ligne correspondante existe, ou à insérer les données en tant que nouvelle ligne si aucune ligne correspondante n'existe. Cela s'effectue habituellement en passant des paramètres à une procédure stockée qui contient les instructions UPDATE et INSERT appropriées. Avec l'instruction MERGE, vous pouvez effectuer les deux tâches dans une instruction unique. L'exemple suivant illustre une procédure stockée qui contient à la fois une instruction INSERT et une instruction UPDATE dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. La procédure est ensuite modifiée pour effectuer les opérations équivalentes à l'aide d'une seule instruction MERGE.  
  
```  
CREATE PROCEDURE dbo.InsertUnitMeasure  
    @UnitMeasureCode nchar(3),  
    @Name nvarchar(25)  
AS   
BEGIN  
    SET NOCOUNT ON;  
-- Update the row if it exists.      
    UPDATE Production.UnitMeasure  
SET Name = @Name  
WHERE UnitMeasureCode = @UnitMeasureCode  
-- Insert the row if the UPDATE statement failed.  
IF (@@ROWCOUNT = 0 )  
BEGIN  
    INSERT INTO Production.UnitMeasure (UnitMeasureCode, Name)  
    VALUES (@UnitMeasureCode, @Name)  
END  
END;  
GO  
-- Test the procedure and return the results.  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'Test Value';  
SELECT UnitMeasureCode, Name FROM Production.UnitMeasure  
WHERE UnitMeasureCode = 'ABC';  
GO  
  
-- Rewrite the procedure to perform the same operations using the 
-- MERGE statement.  
-- Create a temporary table to hold the updated or inserted values 
-- from the OUTPUT clause.  
CREATE TABLE #MyTempTable  
    (ExistingCode nchar(3),  
     ExistingName nvarchar(50),  
     ExistingDate datetime,  
     ActionTaken nvarchar(10),  
     NewCode nchar(3),  
     NewName nvarchar(50),  
     NewDate datetime  
    );  
GO  
ALTER PROCEDURE dbo.InsertUnitMeasure  
    @UnitMeasureCode nchar(3),  
    @Name nvarchar(25)  
AS   
BEGIN  
    SET NOCOUNT ON;  
  
    MERGE Production.UnitMeasure AS target  
    USING (SELECT @UnitMeasureCode, @Name) AS source (UnitMeasureCode, Name)  
    ON (target.UnitMeasureCode = source.UnitMeasureCode)  
    WHEN MATCHED THEN   
        UPDATE SET Name = source.Name  
WHEN NOT MATCHED THEN  
    INSERT (UnitMeasureCode, Name)  
    VALUES (source.UnitMeasureCode, source.Name)  
    OUTPUT deleted.*, $action, inserted.* INTO #MyTempTable;  
END;  
GO  
-- Test the procedure and return the results.  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'New Test Value';  
EXEC InsertUnitMeasure @UnitMeasureCode = 'XYZ', @Name = 'Test Value';  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'Another Test Value';  
  
SELECT * FROM #MyTempTable;  
-- Cleanup   
DELETE FROM Production.UnitMeasure WHERE UnitMeasureCode IN ('ABC','XYZ');  
DROP TABLE #MyTempTable;  
GO  
```  
  
### <a name="b-using-merge-to-perform-update-and-delete-operations-on-a-table-in-a-single-statement"></a>B. Utilisation de MERGE pour effectuer des opérations UPDATE et DELETE sur une table dans une instruction unique  
 L'exemple suivant utilise la clause MERGE pour mettre quotidiennement à jour la table `ProductInventory` dans l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], selon les commandes traitées dans la table `SalesOrderDetail`. La colonne `Quantity` de la table `ProductInventory` est mise à jour en soustrayant le nombre de commandes passées chaque jour pour chaque produit dans la table `SalesOrderDetail`. Si le nombre de commandes concernant un produit est tel que le stock de ce produit tombe à 0 ou en dessous de cette valeur, la ligne correspondant à ce produit est supprimée de la table `ProductInventory`.  
  
```  
CREATE PROCEDURE Production.usp_UpdateInventory  
    @OrderDate datetime  
AS  
MERGE Production.ProductInventory AS target  
USING (SELECT ProductID, SUM(OrderQty) FROM Sales.SalesOrderDetail AS sod  
    JOIN Sales.SalesOrderHeader AS soh  
    ON sod.SalesOrderID = soh.SalesOrderID  
    AND soh.OrderDate = @OrderDate  
    GROUP BY ProductID) AS source (ProductID, OrderQty)  
ON (target.ProductID = source.ProductID)  
WHEN MATCHED AND target.Quantity - source.OrderQty <= 0  
    THEN DELETE  
WHEN MATCHED   
    THEN UPDATE SET target.Quantity = target.Quantity - source.OrderQty,   
                    target.ModifiedDate = GETDATE()  
OUTPUT $action, Inserted.ProductID, Inserted.Quantity, 
    Inserted.ModifiedDate, Deleted.ProductID,  
    Deleted.Quantity, Deleted.ModifiedDate;  
GO  
  
EXECUTE Production.usp_UpdateInventory '20030501'  
```  
  
### <a name="c-using-merge-to-perform-update-and-insert-operations-on-a-target-table-by-using-a-derived-source-table"></a>C. Utilisation de l'instruction MERGE pour effectuer des opérations UPDATE et INSERT sur une table cible à l'aide d'une table source dérivée  
 L'exemple suivant utilise l'instruction MERGE pour modifier la table `SalesReason` en mettant à jour ou en insérant des lignes dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Lorsque la valeur de `NewName` dans la table source correspond à une valeur de la colonne `Name` dans la table cible, (`SalesReason`), la colonne `ReasonType` est mise à jour dans la table cible. Lorsque la valeur de `NewName` ne correspond à aucune autre valeur, la ligne source est insérée dans la table cible. La table source est une table dérivée qui utilise le constructeur de valeurs de table [!INCLUDE[tsql](../../includes/tsql-md.md)] afin de spécifier plusieurs lignes pour la table source. Pour plus d’informations sur l’utilisation du constructeur de valeurs de table dans une table dérivée, consultez [constructeur de valeurs de Table &#40; Transact-SQL &#41; ](../../t-sql/queries/table-value-constructor-transact-sql.md). Cet exemple montre également comment stocker les résultats de la clause OUTPUT dans une variable de table, puis résumer les résultats de l'instruction MERGE en effectuant une opération Select simple qui retourne le nombre de lignes insérées ou mises à jour.  
  
```  
-- Create a temporary table variable to hold the output actions.  
DECLARE @SummaryOfChanges TABLE(Change VARCHAR(20));  
  
MERGE INTO Sales.SalesReason AS Target  
USING (VALUES ('Recommendation','Other'), ('Review', 'Marketing'), 
              ('Internet', 'Promotion'))  
       AS Source (NewName, NewReasonType)  
ON Target.Name = Source.NewName  
WHEN MATCHED THEN  
UPDATE SET ReasonType = Source.NewReasonType  
WHEN NOT MATCHED BY TARGET THEN  
INSERT (Name, ReasonType) VALUES (NewName, NewReasonType)  
OUTPUT $action INTO @SummaryOfChanges;  
  
-- Query the results of the table variable.  
SELECT Change, COUNT(*) AS CountPerChange  
FROM @SummaryOfChanges  
GROUP BY Change;  
```  
  
### <a name="d-inserting-the-results-of-the-merge-statement-into-another-table"></a>D. Insertion des résultats de l'instruction MERGE dans une autre table  
 L'exemple suivant capture les données retournées par la clause OUTPUT d'une instruction MERGE et insère ces données dans une autre table. L’instruction MERGE met à jour la colonne `Quantity` de la table `ProductInventory` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] selon les commandes traitées dans la table `SalesOrderDetail`. L'exemple capture les lignes qui sont mises à jour et les insère dans une autre table utilisée pour suivre les modifications de stock.  
  
```  
CREATE TABLE Production.UpdatedInventory  
    (ProductID INT NOT NULL, LocationID int, NewQty int, PreviousQty int,  
     CONSTRAINT PK_Inventory PRIMARY KEY CLUSTERED (ProductID, LocationID));  
GO  
INSERT INTO Production.UpdatedInventory  
SELECT ProductID, LocationID, NewQty, PreviousQty   
FROM  
(    MERGE Production.ProductInventory AS pi  
     USING (SELECT ProductID, SUM(OrderQty)   
            FROM Sales.SalesOrderDetail AS sod  
            JOIN Sales.SalesOrderHeader AS soh  
            ON sod.SalesOrderID = soh.SalesOrderID  
            AND soh.OrderDate BETWEEN '20030701' AND '20030731'  
            GROUP BY ProductID) AS src (ProductID, OrderQty)  
     ON pi.ProductID = src.ProductID  
    WHEN MATCHED AND pi.Quantity - src.OrderQty >= 0   
        THEN UPDATE SET pi.Quantity = pi.Quantity - src.OrderQty  
    WHEN MATCHED AND pi.Quantity - src.OrderQty <= 0   
        THEN DELETE  
    OUTPUT $action, Inserted.ProductID, Inserted.LocationID, 
        Inserted.Quantity AS NewQty, Deleted.Quantity AS PreviousQty)  
 AS Changes (Action, ProductID, LocationID, NewQty, PreviousQty) 
 WHERE Action = 'UPDATE';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Clause OUTPUT &#40; Transact-SQL &#41;](../../t-sql/queries/output-clause-transact-sql.md)   
 [FUSIONNER des Packages Integration Services](../../integration-services/control-flow/merge-in-integration-services-packages.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [Constructeur de valeurs de table &#40; Transact-SQL &#41;](../../t-sql/queries/table-value-constructor-transact-sql.md)  
  
  

