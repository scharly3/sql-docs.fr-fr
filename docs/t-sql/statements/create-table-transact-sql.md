---
title: "CRÉER la TABLE (Transact-SQL) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILESTREAM_TSQL
- TABLE
- CREATE_TABLE_TSQL
- CREATE TABLE
- FILESTREAM
- TABLE_TSQL
- FILESTREAM_ON
- FILESTREAM_ON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CHECK constraints
- global temporary tables [SQL Server]
- local temporary tables [SQL Server]
- size [SQL Server], tables
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], columns
- maximum number of indexes per table
- number of tables per database
- number of indexes per table
- table creation [SQL Server], CREATE TABLE
- temporary tables [SQL Server], creating
- table size [SQL Server]
- nullability [SQL Server]
- partitioned tables [SQL Server], creating
- DEFAULT definition
- null values [SQL Server], columns
- number of rows per table
- maximum number of columns per table
- FOREIGN KEY constraints, creating
- PRIMARY KEY constraints
- number of bytes per row
- CREATE TABLE statement
- number of columns per table
- maximum number of bytes per row
ms.assetid: 1e068443-b9ea-486a-804f-ce7b6e048e8b
caps.latest.revision: 256
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0978041b1c2683f6af3f6c531ddc10edc6b9bcbf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-transact-sql"></a>CREATE TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crée une nouvelle table dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
> [!NOTE]   
>  Pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] syntaxe, consultez [CREATE TABLE (Azure SQL Data Warehouse)](../../t-sql/statements/create-table-azure-sql-data-warehouse.md).
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
--Simple CREATE TABLE Syntax (common if not using options)  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    ( { <column_definition> } [ ,...n ] )   
[ ; ]  
```  
  
## <a name="syntax"></a>Syntaxe  
  
```  
--Disk-Based CREATE TABLE Syntax  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    [ AS FileTable ]  
    ( {   <column_definition>   
        | <computed_column_definition>    
        | <column_set_definition>   
        | [ <table_constraint> ]   
        | [ <table_index> ] }  
          [ ,...n ]    
          [ PERIOD FOR SYSTEM_TIME ( system_start_time_column_name   
             , system_end_time_column_name ) ]  
      )  
    [ ON { partition_scheme_name ( partition_column_name )   
           | filegroup   
           | "default" } ]   
    [ TEXTIMAGE_ON { filegroup | "default" } ]   
    [ FILESTREAM_ON { partition_scheme_name   
           | filegroup   
           | "default" } ]  
    [ WITH ( <table_option> [ ,...n ] ) ]  
[ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ FILESTREAM ]  
    [ COLLATE collation_name ]   
    [ SPARSE ]  
    [ MASKED WITH ( FUNCTION = ' mask_function ') ]  
    [ CONSTRAINT constraint_name [ DEFAULT constant_expression ] ]   
    [ IDENTITY [ ( seed,increment ) ]  
    [ NOT FOR REPLICATION ]   
    [ GENERATED ALWAYS AS ROW { START | END } [ HIDDEN ] ]   
    [ NULL | NOT NULL ]  
    [ ROWGUIDCOL ]  
    [ ENCRYPTED WITH   
        ( COLUMN_ENCRYPTION_KEY = key_name ,  
          ENCRYPTION_TYPE = { DETERMINISTIC | RANDOMIZED } ,   
          ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
        ) ]  
    [ <column_constraint> [ ...n ] ]   
    [ <column_index> ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
        [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
[ CONSTRAINT constraint_name ]   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH FILLFACTOR = fillfactor    
          | WITH ( < index_option > [ , ...n ] )   
        ]   
        [ ON { partition_scheme_name ( partition_column_name )   
            | filegroup | "default" } ]  
  
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
  
  | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
}   
  
<column_index> ::=   
 INDEX index_name [ CLUSTERED | NONCLUSTERED ]  
    [ WITH ( <index_option> [ ,... n ] ) ]  
    [ ON { partition_scheme_name (column_name )   
         | filegroup_name  
         | default   
         }  
    ]   
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]  
  
<computed_column_definition> ::=  
column_name AS computed_column_expression   
[ PERSISTED [ NOT NULL ] ]  
[   
    [ CONSTRAINT constraint_name ]  
    { PRIMARY KEY | UNIQUE }  
        [ CLUSTERED | NONCLUSTERED ]  
        [   
            WITH FILLFACTOR = fillfactor   
          | WITH ( <index_option> [ , ...n ] )  
        ]  
        [ ON { partition_scheme_name ( partition_column_name )   
        | filegroup | "default" } ]  
  
    | [ FOREIGN KEY ]   
        REFERENCES referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE } ]   
        [ ON UPDATE { NO ACTION } ]   
        [ NOT FOR REPLICATION ]   
  
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
]   
  
<column_set_definition> ::=  
column_set_name XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
  
< table_constraint > ::=  
[ CONSTRAINT constraint_name ]   
{   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        (column [ ASC | DESC ] [ ,...n ] )   
        [   
            WITH FILLFACTOR = fillfactor   
           |WITH ( <index_option> [ , ...n ] )   
        ]  
        [ ON { partition_scheme_name (partition_column_name)  
            | filegroup | "default" } ]   
    | FOREIGN KEY   
        ( column [ ,...n ] )   
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )  
 

  
< table_index > ::=   
{  
    {  
      INDEX index_name [ CLUSTERED | NONCLUSTERED ]   
         (column_name [ ASC | DESC ] [ ,... n ] )   
    | INDEX index_name CLUSTERED COLUMNSTORE  
    | INDEX index_name [ NONCLUSTERED ] COLUMNSTORE (column_name [ ,... n ] )  
    }  
    [ WITH ( <index_option> [ ,... n ] ) ]   
    [ ON { partition_scheme_name (column_name )   
         | filegroup_name  
         | default   
         }  
    ]   
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]  
  
}   


<table_option> ::=  
{  
    [DATA_COMPRESSION = { NONE | ROW | PAGE }  
      [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
      [ , ...n ] ) ]]  
    [ FILETABLE_DIRECTORY = <directory_name> ]   
    [ FILETABLE_COLLATE_FILENAME = { <collation_name> | database_default } ]  
    [ FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME = <constraint_name> ]  
    [ FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME = <constraint_name> ]  
    [ FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME = <constraint_name> ]  
    [ SYSTEM_VERSIONING = ON [ ( HISTORY_TABLE = schema_name . history_table_name  
        [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] ) ] ]  
    [ REMOTE_DATA_ARCHIVE =   
      {   
          ON [ ( <table_stretch_options> [,...n] ) ]  
        | OFF ( MIGRATION_STATE = PAUSED )   
      }   
    ]  
}  
  
<table_stretch_options> ::=  
{  
     [ FILTER_PREDICATE = { null | table_predicate_function } , ]  
       MIGRATION_STATE = { OUTBOUND | INBOUND | PAUSED }  
 }  
  
<index_option> ::=  
{   
    PAD_INDEX = { ON | OFF }   
  | FILLFACTOR = fillfactor   
  | IGNORE_DUP_KEY = { ON | OFF }   
  | STATISTICS_NORECOMPUTE = { ON | OFF }   
  | ALLOW_ROW_LOCKS = { ON | OFF}   
  | ALLOW_PAGE_LOCKS ={ ON | OFF}   
  | COMPRESSION_DELAY= {0 | delay [Minutes]}  
  | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
       [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
       [ , ...n ] ) ]  
}  
<range> ::=   
<partition_number_expression> TO <partition_number_expression>  
```  
  
```  
  
      --Memory optimized CREATE TABLE Syntax  
CREATE TABLE  
    [database_name . [schema_name ] . | schema_name . ] table_name  
    ( { <column_definition>  
    | [ <table_constraint> ] [ ,... n ]  
    | [ <table_index> ]  
      [ ,... n ] }   
      [ PERIOD FOR SYSTEM_TIME ( system_start_time_column_name   
        , system_end_time_column_name ) ]  
)  
    [ WITH ( <table_option> [ ,... n ] ) ]  
 [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]  
    [ GENERATED ALWAYS AS ROW { START | END } [ HIDDEN ] ]   
    [ NULL | NOT NULL ]  
[  
    [ CONSTRAINT constraint_name ] DEFAULT memory_optimized_constant_expression ]  
    | [ IDENTITY [ ( 1, 1 ) ]  
]  
    [ <column_constraint> ]  
    [ <column_index> ]  
  
<data type> ::=  
 [type_schema_name . ] type_name [ (precision [ , scale ]) ]  
  
<column_constraint> ::=  
 [ CONSTRAINT constraint_name ]  
{   
  { PRIMARY KEY | UNIQUE }    
      {   NONCLUSTERED   
        | NONCLUSTERED HASH WITH (BUCKET_COUNT = bucket_count)   
      }   
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
  | CHECK ( logical_expression )   
}  
  
< table_constraint > ::=  
 [ CONSTRAINT constraint_name ]  
{    
   { PRIMARY KEY | UNIQUE }  
     {   
       NONCLUSTERED (column [ ASC | DESC ] [ ,... n ])  
       | NONCLUSTERED HASH (column [ ,... n ] ) WITH ( BUCKET_COUNT = bucket_count )   
                    }   
    | FOREIGN KEY   
        ( column [ ,...n ] )   
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]   
    | CHECK ( logical_expression )   
}  
  
<column_index> ::=  
  INDEX index_name  
{ [ NONCLUSTERED ] | [ NONCLUSTERED ] HASH WITH (BUCKET_COUNT = bucket_count)  }  
  
<table_index> ::=  
  INDEX index_name  
{   [ NONCLUSTERED ] HASH (column [ ,... n ] ) WITH (BUCKET_COUNT = bucket_count)   
  | [ NONCLUSTERED ] (column [ ASC | DESC ] [ ,... n ] )   
      [ ON filegroup_name | default ]  
  | CLUSTERED COLUMNSTORE [WITH ( COMPRESSION_DELAY = {0 | delay [Minutes]})]  
      [ ON filegroup_name | default ]  
  
}  
  
<table_option> ::=  
{  
    MEMORY_OPTIMIZED = ON   
  | DURABILITY = {SCHEMA_ONLY | SCHEMA_AND_DATA}  
  | SYSTEM_VERSIONING = ON [ ( HISTORY_TABLE = schema_name . history_table_name  
        [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] ) ]   
  
}  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la base de données dans laquelle la table est créée. *database_name* doit spécifier le nom de la base de données existante. Si non spécifié, *nom_base_de_données* par défaut, la base de données actuelle. La connexion pour la connexion actuelle doit être associée à un ID utilisateur existant dans la base de données spécifiée par *nom_base_de_données*, et cet ID utilisateur doit disposer des autorisations CREATE TABLE.  
  
 *schema_name*  
 Nom du schéma auquel appartient la nouvelle table.  
  
 *table_name*  
 Nom de la nouvelle table. Les noms de tables doivent respecter les règles pour [identificateurs](../../relational-databases/databases/database-identifiers.md). *nom_table* peut être un maximum de 128 caractères, à l’exception des noms de tables temporaires locales (noms précédés du signe dièse (#)) qui ne peut pas dépasser 116 caractères.  
  
 AS FileTable 
 
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
 
 Crée la table en tant que FileTable. Vous ne spécifiez pas de colonnes car un FileTable dispose d'un schéma fixe. Pour plus d’informations sur les FileTables, consultez [FileTables &#40; SQL Server &#41; ](../../relational-databases/blob/filetables-sql-server.md).  
  
 *nom_colonne*  
 *computed_column_expression*  
 Expression définissant la valeur d'une colonne calculée. Une colonne calculée est une colonne virtuelle qui n'est pas stockée physiquement dans la table, à moins que la colonne ne soit indiquée comme PERSISTED. La colonne est calculée à partir d'une expression qui utilise d'autres colonnes dans la même table. Par exemple, une colonne calculée peut avoir la définition : **coût** AS **prix** \* **qty**. L'expression peut être un nom de colonne non calculée, une constante, une fonction, une variable et toute combinaison de ces éléments reliés par un ou plusieurs opérateurs. L'expression ne peut pas être une sous-requête ou contenir des types de données d'alias.  
  
 Les colonnes calculées peuvent être utilisées dans des listes de sélection, des clauses WHERE, des clauses ORDER BY ou à tout autre emplacement où il est possible d'utiliser des expressions régulières, aux exceptions suivantes près :  
  
-   Les colonnes calculées doivent être marquées comme PERSISTED pour participer à des contraintes FOREIGN KEY ou CHECK.  
  
-   Une colonne calculée peut être utilisée en tant que colonne clé dans un index ou en tant que partie d’aucune clé primaire ou une contrainte UNIQUE, si la valeur de la colonne calculée est définie par une expression déterministe et que le type de données du résultat est autorisé dans les colonnes d’index.  
  
     Par exemple, si la table possède des colonnes de type integer **un** et **b**, la colonne calculée **a + b** peut être indexée, contrairement à la colonne calculée **a + DATEPART (dd, GETDATE()** ne peut pas être indexée, car la valeur peut changer au fil des appels.  
  
-   Une colonne calculée ne peut pas être la cible d'une instruction INSERT ou UPDATE.  
  
> [!NOTE]  
>  Chaque ligne dans une table peut avoir des valeurs différentes pour les colonnes impliquées dans une colonne calculée ; par conséquent, il est possible que la colonne calculée n'ait pas la même valeur pour chaque ligne.  
  
 En fonction des expressions utilisées, la possibilité de valeurs NULL dans les colonnes calculées est déterminée automatiquement par le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Le résultat de la plupart des expressions est considéré comme pouvant avoir la valeur Null, même si seules des colonnes n'acceptant pas cette valeur sont présentes, car des dépassements négatifs ou positifs possibles produisent également des résultats Null. Utilisez la fonction COLUMNPROPERTY avec la **AllowsNull** propriété pour étudier la possibilité de valeur NULL d’une colonne calculée dans une table. Une expression qui accepte la valeur NULL peut être transformée en une nonnullable en spécifiant ISNULL avec la *check_expression* constante, où la constante est une valeur non nulle substituée à n’importe quel résultat NULL. L'autorisation REFERENCES sur le type est nécessaire pour les colonnes calculées basées sur des expressions de type CLR (Common Language Runtime) défini par l'utilisateur.  
  
 PERSISTED  
 Spécifie que le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] stockera physiquement les valeurs calculées dans la table et qu'il les mettra à jour lorsque les autres colonnes dont dépend la colonne calculée seront actualisées. Notamment, une colonne calculée en tant que PERSISTED vous permet de créer un index sur une colonne calculée qui est déterministe, mais pas précise. Pour plus d'informations, consultez [Indexes on Computed Columns](../../relational-databases/indexes/indexes-on-computed-columns.md). Les colonnes calculées utilisées comme colonnes de partitionnement d'une table partitionnée doivent être marquées comme PERSISTED. *computed_column_expression* doit être déterministe lorsque PERSISTED est spécifié.  
  
 ON { *schéma_partition* | *groupe de fichiers* | **»**par défaut**»** }  

 Spécifie le schéma de partition ou groupe de fichiers dans lequel la table est stockée. Si *schéma_partition* est spécifié, la table doit être une table partitionnée dont les partitions sont stockées sur un ensemble d’un ou plusieurs groupes de fichiers spécifié dans *schéma_partition*. Si *groupe de fichiers* est spécifié, la table est stockée dans le groupe de fichiers nommé. Le groupe de fichiers doit exister dans la base de données. Si **»**par défaut**»** est spécifié, ou si ON n’est pas du tout spécifié, la table est stockée dans le groupe de fichiers par défaut. Le mécanisme de stockage d'une table tel que spécifié dans CREATE TABLE ne peut plus être modifié ultérieurement.  
  
 ON {*schéma_partition* | *groupe de fichiers* | **»**par défaut**»**} peut également être spécifiée dans une contrainte PRIMARY KEY ou UNIQUE. Ces contraintes créent des index. Si *groupe de fichiers* est spécifié, l’index est stocké dans le groupe de fichiers nommé. Si **»**par défaut**»** est spécifié, ou si ON n’est pas du tout spécifié, l’index est stocké dans le même groupe de fichiers que la table. Si la contrainte PRIMARY KEY ou UNIQUE crée un index cluster, les pages de données de la table sont stockées dans le même groupe de fichiers que l'index. Si CLUSTERED est spécifié ou la contrainte crée un index ordonné en clusters et une *schéma_partition* est spécifiée qui diffère la *schéma_partition* ou *groupe de fichiers* de la définition de la table, ou vice versa, seule la définition de contrainte sera honorée et l’autre sera ignorée.  
  
> [!NOTE]  
>  L'élément « default » n'est pas un mot clé dans ce contexte. Il est un identificateur pour le groupe de fichiers par défaut et doit être délimité, comme dans ON **»**par défaut**»** ou ON **[**par défaut**]**. Si **»**par défaut**»** est spécifié, l’option QUOTED_IDENTIFIER doit avoir la valeur ON pour la session active. Il s'agit du paramètre par défaut. Pour plus d’informations, consultez [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
> [!NOTE]  
>  Après avoir créé une table partitionnée, pensez à affecter à l'option LOCK_ESCALATION de la table la valeur AUTO. Cela peut améliorer la concurrence en permettant l'escalade des verrous au niveau de la partition (HoBT) plutôt que de la table. Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
 TEXTIMAGE_ON { *groupe de fichiers*| **»**par défaut**»** }  
 Indique que le **texte**, **ntext**, **image**, **xml**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, et les colonnes de type défini par l’utilisateur CLR (y compris géométrie et géographie) sont stockés sur le groupe de fichiers spécifié.  
  
 TEXTIMAGE_ON n'est pas autorisé s'il n'y a pas de colonne de valeur élevée dans la table. TEXTIMAGE_ON ne peut pas être spécifié si *schéma_partition* est spécifié. Si **»**par défaut**»** est spécifié, ou si TEXTIMAGE_ON n’est pas du tout spécifié, les colonnes de valeur élevée sont stockés dans le groupe de fichiers par défaut. Le stockage de données de colonnes de valeur élevée tel que spécifié dans CREATE TABLE ne peut plus être modifié ultérieurement.  

> [!NOTE]  
> Varchar (max), nvarchar (max), varbinary (max), xml et les valeurs UDT volumineuses sont stockées directement dans la ligne de données, jusqu'à une limite de 8 000 octets et tant que la valeur peut contenir l’enregistrement. Si la valeur ne tient pas dans l’enregistrement, un pointeur est trié dans la ligne et le reste est stocké hors de la ligne dans l’espace de stockage LOB. 0 est la valeur par défaut.
TEXTIMAGE_ON modifie uniquement l’emplacement de le « espace de stockage LOB », cela n’affecte pas lorsque les données sont stockées dans la ligne. Utilisez les types de valeur volumineux en dehors de l’option de ligne de sp_tableoption pour stocker la valeur métier hors de la ligne. 


> [!NOTE]  
>  L'élément « default » n'est pas un mot clé dans ce contexte. Il est un identificateur pour le groupe de fichiers par défaut et doit être délimité, comme dans TEXTIMAGE_ON **»**par défaut**»** ou TEXTIMAGE_ON **[**par défaut**]**. Si **»**par défaut**»** est spécifié, l’option QUOTED_IDENTIFIER doit avoir la valeur ON pour la session active. Il s'agit du paramètre par défaut. Pour plus d’informations, consultez [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 FILESTREAM_ON { *partition_scheme_name* | filegroup | **»**par défaut**»** } **s’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
 
 Spécifie le groupe de fichiers pour les données FILESTREAM.  
  
 Si la table contient des données FILESTREAM et si elle est partitionnée, la clause FILESTREAM_ON doit être incluse et doit spécifier un schéma de partition de groupes de fichiers FILESTREAM. Ce schéma de partition doit utiliser la même fonction de partition et les mêmes colonnes de partition que le schéma de partition de la table, faute de quoi une erreur est générée.  
  
 Si la table n'est pas partitionnée, la colonne FILESTREAM ne peut pas être partitionnée. Les données FILESTREAM de la table doivent être stockées dans un groupe de fichiers unique. Ce groupe de fichiers est spécifié dans la clause FILESTREAM_ON.  
  
 Si la table n'est pas partitionnée et si la clause FILESTREAM_ON n'est pas spécifiée, c'est le groupe de fichiers FILESTREAM dont la propriété DEFAULT est définie qui est utilisé. S'il n'y a aucun groupe de fichiers FILESTREAM, une erreur est générée.  
  
-   Comme avec ON et TEXTIMAGE_ON, la valeur définie à l'aide de CREATE TABLE pour FILESTREAM_ON ne peut pas être modifiée, sauf dans les cas suivants :  
  
-   A [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md) instruction convertit un tas en un index cluster. Dans ce cas, il est possible de spécifier un autre groupe de fichiers FILESTREAM, un autre schéma de partition ou la valeur NULL.  
  
-   A [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md) instruction convertit un index cluster en un segment de mémoire. Dans ce cas, un autre groupe de fichiers FILESTREAM, le schéma de partition ou **»**par défaut**»** peut être spécifié.  
  
 Le groupe de fichiers dans le `FILESTREAM_ON <filegroup>` clause ou chaque groupe de fichiers FILESTREAM nommé dans le schéma de partition doit avoir un fichier défini pour le groupe de fichiers. Ce fichier doit être défini à l’aide un [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) ou [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) instruction ; sinon, une erreur est générée.  
  
 Pour les rubriques FILESTREAM connexes, consultez [objets binaires volumineux &#40; Objet BLOB &#41; Données &#40; SQL Server &#41; ](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 [ *type_schema_name***.** ] *type_name*  
 Précise le type de données de la colonne et le schéma auquel il appartient. Pour les tables sur disque, le type de données peut être l'un des suivants :  
  
-   Type de données système.  
  
-   Type d'alias basé sur un type de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les types de données alias sont créés à l'aide de l'instruction CREATE TYPE avant de pouvoir être utilisés dans la définition d'une table ; L'affectation NULL ou NOT NULL pour un type de données d'alias peut être ignorée au cours de l'exécution de l'instruction CREATE TABLE. Cependant, une spécification de longueur ne peut pas être modifiée ; la longueur d'un type de données d'alias ne peut pas être spécifiée dans une instruction CREATE TABLE.  
  
-   Un type CLR défini par l’utilisateur. Les types de données CLR définis par l'utilisateur sont créés avec l'instruction CREATE TYPE avant de pouvoir être utilisés dans une définition de table. Pour créer une colonne sur un type de données CLR défini par l'utilisateur, une autorisation REFERENCES est nécessaire pour le type.  
  
 Si *type_schema_name* n’est pas spécifié, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] références *type_name* dans l’ordre suivant :  
  
-   Le type de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Le schéma par défaut de l'utilisateur actuel dans la base de données active  
  
-   Schéma **dbo** dans la base de données active.  
  
 Pour les tables optimisées en mémoire, consultez [prise en charge des Types de données pour OLTP en mémoire](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md) pour obtenir la liste des types de système pris en charge.  
  
 *precision*  
 Précision du type de données spécifié. Pour plus d’informations sur les valeurs de précision valides, consultez [précision, échelle et longueur](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 *scale*  
 Échelle du type de données spécifié. Pour plus d’informations sur les valeurs d’échelle valides, consultez [précision, échelle et longueur](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 **max**  
 S’applique uniquement à la **varchar**, **nvarchar**, et **varbinary** des types de données pour le stockage de 2 ^ 31 octets de caractères et les données binaires et 2 ^ 30 octets de données Unicode.  
  
 CONTENT  
 Spécifie que chaque instance de la **xml** de type de données dans *column_name* peut contenir plusieurs éléments de niveau supérieur. Le contenu s’applique uniquement à la **xml** données de type et peut être spécifié uniquement si *xml_schema_collection* est également spécifié. En l'absence de toute spécification, CONTENT est le comportement par défaut.  
  
 DOCUMENT  
 Spécifie que chaque instance de la **xml** de type de données dans *column_name* peut contenir qu’un seul élément de niveau supérieur. DOCUMENT s’appliquent uniquement à la **xml** données de type et peut être spécifié uniquement si *xml_schema_collection* est également spécifié.  
  
 *xml_schema_collection*  
 S’applique uniquement à la **xml** type de données de l’association de collection de schémas XML avec le type. Avant de taper un **xml** colonne à un schéma, le schéma doit d’abord être créé dans la base de données à l’aide de [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md).  
  
 DEFAULT  
 Spécifie la valeur fournie pour la colonne lorsque vous n'avez pas spécifié explicitement de valeur lors d'une insertion. Définitions DEFAULT peuvent être appliquées à toutes les colonnes à l’exception de celles définies en tant que **timestamp**, ou ceux dont la propriété d’identité. Si une valeur par défaut est spécifiée pour une colonne de type défini par l’utilisateur, le type doit prendre en charge une conversion implicite de *expression_constante* pour le type défini par l’utilisateur. Les définitions de valeurs par défaut sont supprimées lorsque la table est supprimée. Seule une valeur constante, telle qu'une chaîne de caractères, une fonction scalaire (fonction système, définie par l'utilisateur ou CLR) ou la valeur NULL peut être utilisée comme valeur par défaut. Pour maintenir la compatibilité avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un nom de contrainte peut être affecté à une définition DEFAULT.  
  
 *expression_constante*  
 Constante, valeur NULL ou fonction système utilisée comme valeur par défaut pour la colonne.  
  
 *memory_optimized_constant_expression*  
 Constante, valeur NULL ou fonction système prise en charge comme valeur par défaut pour la colonne. Doit être prise en charge dans les procédures stockées compilées en mode natif. Pour plus d’informations sur les fonctions intégrées dans les procédures stockées compilées en mode natif, consultez [fonctionnalités prises en charge pour la compilation en mode natif les Modules T-SQL](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
 IDENTITY  
 Indique que la nouvelle colonne est une colonne d'identité. Lorsqu'une ligne est ajoutée à la table, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] affecte une valeur incrémentée unique à la colonne. Les colonnes d'identité sont normalement utilisées avec les contraintes PRIMARY KEY comme identificateur de ligne unique pour la table. La propriété IDENTITY peut être affectée à **tinyint**, **smallint**, **int**, **bigint**, **decimal(p,0)**, ou **numeric(p,0)** colonnes. Une seule colonne d'identité peut être créée par table. Il n'est pas possible d'utiliser des valeurs par défaut liées et des contraintes DEFAULT avec une colonne d'identité. Vous devez spécifier à la fois la valeur initiale et l'incrément ou aucune de ces valeurs. Si vous n'en spécifiez aucun, la valeur par défaut est (1,1).  
  
 Dans une table optimisée en mémoire, la seule valeur autorisée pour les deux *seed* et *incrément* est 1 ; (1,1) est la valeur par défaut pour *seed* et *incrément*.  
  
 *valeur initiale*  
 Valeur utilisée pour la toute première ligne chargée dans la table.  
  
 *incrément*  
 Est la valeur d’incrément ajoutée à la valeur d’identité de la ligne précédemment chargée.  
  
 NOT FOR REPLICATION  
 Dans l'instruction CREATE TABLE, la clause NOT FOR REPLICATION peut être spécifiée pour la propriété IDENTITY, les contraintes FOREIGN KEY et CHECK. Si la clause est spécifiée pour la propriété IDENTITY, les valeurs ne sont pas incrémentées dans les colonnes d'identité lorsque les agents de réplication effectuent des insertions. Si cette clause est spécifiée pour une contrainte, la contrainte n'est pas appliquée lorsque les agents de réplication effectuent des opérations d'insertion, de mise à jour ou de suppression.  
  
 GENERATED ALWAYS AS LIGNE {DÉMARRER | FIN} [MASQUÉ] [NON NULL]  
 **S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Spécifie qu’une colonne de type datetime2 spécifié sera utilisée par le système enregistre l’heure de début pour laquelle un enregistrement est valide ou de l’heure de fin pour laquelle un enregistrement est valide. La colonne doit être définie comme NOT NULL. Si vous essayez de les spécifier comme NULL, le système génère une erreur. Si vous ne spécifiez pas explicitement NOT NULL pour une colonne de période, le système est de définir la colonne comme NOT NULL par défaut. Utilisez cet argument conjointement avec l’instruction PERIOD FOR SYSTEM_TIME et avec SYSTEM_VERSIONING = ON arguments pour activer le contrôle de version système sur une table. Pour plus d’informations, voir [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
 Vous pouvez marquer un ou deux colonnes de période avec **masqué** indicateur implicitement masquer ces colonnes telles que **sélectionnez \* FROM**  *`<table>`*  ne retourne pas une valeur pour ces colonnes. Par défaut, les colonnes de période ne sont pas masqués. Pour pouvoir être utilisé, les colonnes masquées doivent être explicitement inclus dans toutes les requêtes qui font directement référencent à la table temporelle. Pour modifier la **masqué** attribut pour une colonne de période existante, **période** doit être supprimé et recréé avec un indicateur masqué différents.  
  
 `INDEX *index_name* [ CLUSTERED | NONCLUSTERED ] (*column_name* [ ASC | DESC ] [ ,... *n* ] )`  
     
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].

Spécifie pour créer un index sur la table. Il peut s’agir d’un index cluster ou un index non cluster. L’index contient les colonnes indiquées et allez trier les données dans l’ordre croissant ou décroissant.  
  
 INDEX *index_name* CLUSTERED COLUMNSTORE  
   
  
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Spécifie de stocker la table entière sous forme de colonnes avec un index cluster columnstore. Cela inclut toujours toutes les colonnes de la table. Les données ne sont pas triées par ordre alphabétique ou numérique, car les lignes sont organisées pour bénéficier des avantages de la compression de columnstore.  
  
 INDEX *index_name* [NONCLUSTERED] COLUMNSTORE (*column_name* [,...*n* ] )  
   
  
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Spécifie pour créer un index non cluster sur la table. La table sous-jacente peut être un segment de mémoire rowstore ou d’un index ordonné en clusters, ou il peut être un index cluster columnstore. Dans tous les cas, la création d’un index non cluster sur une table stocke une deuxième copie des données pour les colonnes dans l’index.  
  
 L’index non cluster est stocké et géré en tant qu’un index cluster columnstore. Elle est appelée pour un index non cluster, car les colonnes peuvent être limités, et il existe en tant qu’un index secondaire sur une table.  
  
 ON *partition_scheme_name***(***column_name***)**  
 Spécifie le schéma de partition qui définit les groupes de fichiers auxquels les partitions d'un index partitionné seront mappées. Le schéma de partition doit exister dans la base de données en exécutant soit [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md) ou [ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md). *column_name* spécifie la colonne sur laquelle un index partitionné sera partitionné. Cette colonne doit correspondre au type de données, longueur, et la précision de l’argument de la partition de fonction qui *partition_scheme_name* est à l’aide. *column_name* n’est pas limité aux colonnes dans la définition d’index. N’importe quelle colonne dans la table de base peut être spécifié, sauf lors du partitionnement d’un index UNIQUE, *column_name* doit être choisie parmi celles qui sont utilisées comme clé unique. Cette restriction permet au [!INCLUDE[ssDE](../../includes/ssde-md.md)] de vérifier l'unicité des valeurs de clés dans une seule partition uniquement.  
  
> [!NOTE]  
>  Lorsque vous partitionnez un index cluster non unique, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ajoute par défaut la colonne de partitionnement à la liste des clés d'index cluster, si elle n'est pas déjà spécifiée. Lorsque vous partitionnez un index non cluster non unique, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ajoute la colonne de partitionnement sous la forme d'une colonne (incluse) non clé de l'index, si elle n'est pas déjà spécifiée.  
  
 Si *partition_scheme_name* ou *groupe de fichiers* n’est pas spécifié et que la table est partitionnée, l’index est placé dans le même schéma de partition à l’aide de la même colonne de partitionnement que la table sous-jacente.  
  
> [!NOTE]  
>  Vous ne pouvez pas spécifier un schéma de partitionnement dans un index XML. Si la table de base est partitionnée, l'index XML utilise le même schéma de partition que la table.  
  
 Pour plus d’informations sur le partitionnement d’index, [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
 ON *filegroup_name*  
 Crée l'index spécifié dans le groupe de fichiers spécifié. Si aucun emplacement n'est défini et que la table ou la vue n'est pas partitionnée, l'index utilise le même groupe de fichiers que la table ou la vue sous-jacente. Le groupe de fichiers doit déjà exister.  
  
 ON **»**par défaut**»**  
 Crée l'index spécifié sur le groupe de fichiers par défaut.  
  
 Le terme « default », dans ce contexte, n'est pas un mot clé. Il est un identificateur pour le groupe de fichiers par défaut et doit être délimité, comme dans ON **»**par défaut**»** ou ON **[**par défaut**]**. Si "default" est spécifié, l'option QUOTED_IDENTIFIER doit être activée (ON) pour la session active. Il s'agit du paramètre par défaut. Pour plus d’informations, consultez [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 [FILESTREAM_ON { *filestream_filegroup_name* | *partition_scheme_name* | « NULL »}]  
   
**S'applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion.md)].

 Spécifie le positionnement de données FILESTREAM pour la table lorsqu'un index cluster est créé. La clause FILESTREAM_ON permet le déplacement des données FILESTREAM vers un schéma de partition ou un groupe de fichiers FILESTREAM différent.  
  
 *filestream_filegroup_name* est le nom du groupe de fichiers FILESTREAM. Le groupe de fichiers doit avoir un fichier défini pour le groupe de fichiers en utilisant un [créer la base de données](../../t-sql/statements/create-database-sql-server-transact-sql.md) ou [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) instruction ; sinon, une erreur est générée.  
  
 Si la table est partitionnée, la clause FILESTREAM_ON doit être incluse et doit spécifier un schéma de partition de groupes de fichiers FILESTREAM qui utilise les mêmes fonctions de partition et colonnes de partition que le schéma de partition pour la table. Dans le cas contraire, une erreur est générée.  
  
 Si la table n'est pas partitionnée, la colonne FILESTREAM ne peut pas être partitionnée. Les données FILESTREAM pour la table doivent être stockées dans un groupe de fichiers unique spécifié dans la clause FILESTREAM_ON.  
  
 FILESTREAM_ON NULL peut être spécifié dans une instruction CREATE INDEX si un index cluster est créé et si la table ne contient pas de colonne FILESTREAM.  
  
 Pour plus d’informations, consultez [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md).  
  
 ROWGUIDCOL  
 Indique que la nouvelle colonne est une colonne d'identité ROWGUID. Seul **uniqueidentifier** colonne par table peut être désignée comme colonne ROWGUIDCOL. L'application de la propriété ROWGUIDCOL permet à la colonne d'être référencée à l'aide de $ROWGUID. La propriété ROWGUIDCOL peut être affectée qu’à un **uniqueidentifier** colonne. Les colonnes avec un type de données défini par l'utilisateur ne peuvent pas être conçues avec ROWGUIDCOL.  
  
 La propriété ROWGUIDCOL n'assure pas l'unicité des valeurs stockées dans la colonne. ROWGUIDCOL ne peut pas non plus générer automatiquement des valeurs pour les nouvelles lignes insérées dans la table. Pour générer des valeurs uniques pour chaque colonne, soit utiliser le [NEWID](../../t-sql/functions/newid-transact-sql.md) ou [NEWSEQUENTIALID](../../t-sql/functions/newsequentialid-transact-sql.md) fonctionnent sur [insérer](../../t-sql/statements/insert-transact-sql.md) instructions ou d’utiliser ces fonctions en tant que la valeur par défaut pour la colonne.  
  
 CHIFFRÉ AVEC  
 Spécifie les colonnes de chiffrement à l’aide de la [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) fonctionnalité.  
  
 COLUMN_ENCRYPTION_KEY = *key_name*  
 Spécifie la clé de chiffrement de colonne. Pour plus d’informations, consultez [CREATE COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-column-encryption-key-transact-sql.md).  
  
 ENCRYPTION_TYPE = {DÉTERMINISTE | ALÉATOIRE}  
 Le**chiffrement déterministe** utilise une méthode qui génère toujours la même valeur chiffrée pour une valeur de texte brut donnée. À l’aide du chiffrement déterministe permet de rechercher à l’aide de la comparaison d’égalité, le regroupement et la jointure de tables à l’aide de jointures d’égalité en fonction des valeurs chiffrées, mais permettre également autoriser les utilisateurs non autorisés de deviner des informations sur les valeurs chiffrées en examinant les séquences dans la colonne chiffrée. Jointure de deux tables sur des colonnes chiffrées de façon déterministe n’est possible si les deux colonnes sont chiffrées à l’aide de la même clé de chiffrement de colonne. Le chiffrement déterministe doit utiliser un classement de colonne avec un ordre de tri binaire 2 pour les colonnes de type caractère.  
  
 Le**chiffrement aléatoire** utilise une méthode qui chiffre les données de manière moins prévisible. Chiffrement aléatoire est plus sécurisé, mais il empêche les recherches d’égalité, le regroupement et la jointure sur les colonnes chiffrées. Colonnes à l’aide d’un chiffrement aléatoire ne peuvent pas être indexées.  
  
 Utilisez le chiffrement déterministe pour les colonnes qui seront les paramètres de recherche ou des paramètres de regroupement, par exemple un numéro d’identification gouvernemental. Utilisez le chiffrement aléatoire, pour les données telles qu’un numéro de carte de crédit, qui est non regroupé avec d’autres enregistrements, ou utilisé pour joindre des tables, et qui n’est pas examiné pour, car vous utilisez d’autres colonnes (par exemple, un numéro de transaction) pour rechercher la ligne qui contient la colonne chiffrée d’intérêt.  
  
 Colonnes doivent être d’un type de données qualifié.  
  
 ALGORITHME  
 Doit être **« AEAD_AES_256_CBC_HMAC_SHA_256 »**.  
  
 Pour plus d’informations, y compris les contraintes de fonctionnalité, consultez [Always Encrypted &#40; moteur de base de données &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
  
 **S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 SPARSE  
 Indique que la nouvelle colonne est une colonne éparse. Le stockage des colonnes éparses est optimisé pour les valeurs Null. Les colonnes éparses ne peuvent pas être désignées comme NOT NULL. Pour plus d’informations sur les colonnes éparses et les restrictions supplémentaires, consultez [utiliser des colonnes éparses](../../relational-databases/tables/use-sparse-columns.md).  
  
 MASQUÉ avec (fonction = ' *mask_function* ')  
 **S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie un masque dynamique des données. *mask_function* est le nom de la fonction de masquage avec les paramètres appropriés. Trois fonctions sont disponibles :  
  
-   () par défaut  
  
-   email()  
  
-   partial()  
  
-   Random()  
  
 Pour les paramètres de fonction, consultez [masquage dynamique des données](../../relational-databases/security/dynamic-data-masking.md).  
  
 FILESTREAM  
   
**S'applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion.md)].

 Valide uniquement pour les **varbinary (max)** colonnes. Spécifie le stockage FILESTREAM pour la **varbinary (max)** données BLOB.  
  
 La table doit également contenir une colonne de la **uniqueidentifier** type de données qui a l’attribut ROWGUIDCOL. Cette colonne ne doit pas autoriser les valeurs Null et doit avoir une contrainte de colonne unique de type UNIQUE ou PRIMARY KEY. La valeur GUID pour la colonne doit être fournie par une application lors de l’insertion de données, ou par une contrainte par défaut qui utilise la fonction NEWID ().  
  
 La colonne ROWGUIDCOL ne peut pas être supprimée et les contraintes liées ne peuvent pas être modifiées tant qu'une colonne FILESTREAM est définie pour la table. La colonne ROWGUIDCOL peut être supprimée uniquement lorsque la dernière colonne FILESTREAM a été supprimée.  
  
 Lorsque l'attribut de stockage FILESTREAM est spécifié pour une colonne, toutes les valeurs de cette colonne sont stockées dans un conteneur de données FILESTREAM sur le système de fichiers.  
  
 COLLATE *collation_name*  
 Indique le classement de la colonne. Nom du classement peut être un nom de classement Windows ou un nom de classement SQL. *collation_name* s’applique uniquement aux colonnes de la **char**, **varchar**, **texte**, **nchar**, **nvarchar**, et **ntext** des types de données. Si cette valeur n'est pas spécifiée, la colonne reçoit le classement du type de données utilisateur, si son type de données est un type de données utilisateur, ou le classement par défaut de la base de données.  
  
 Pour plus d’informations sur les noms de classements Windows et SQL, consultez [nom de classement Windows](../../t-sql/statements/windows-collation-name-transact-sql.md) et [nom de classement SQL](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 Pour plus d’informations sur la clause COLLATE, consultez [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 CONSTRAINT  
 Mot clé facultatif qui indique le début de la définition d'une contrainte PRIMARY KEY, NOT NULL, UNIQUE, FOREIGN KEY ou CHECK.  
  
 *constraint_name*  
 Est le nom d’une contrainte. Les noms de contraintes doivent être uniques au sein du schéma auquel appartient la table.  
  
 NULL | NOT NULL  
 Déterminer si les valeurs null sont autorisées dans la colonne. NULL n'est pas strictement une contrainte, mais peut être spécifié comme NOT NULL. Il est possible de spécifier NOT NULL pour des colonnes calculées seulement si PERSISTED est également spécifié.  
  
 PRIMARY KEY  
 Contrainte assurant l'intégrité d'entité d'une ou de plusieurs colonnes spécifiées au moyen d'un index unique. Une seule contrainte PRIMARY KEY peut être créée par table.  
  
 UNIQUE  
 Contrainte assurant l'intégrité de l'entité d'une colonne ou de plusieurs colonnes spécifiées au moyen d'un index unique. Une table peut comprendre plusieurs contraintes UNIQUE.  
  
 CLUSTERED et NONCLUSTERED  
 Indique qu'un index, cluster ou non cluster, est créé pour la contrainte PRIMARY KEY ou UNIQUE. Les contraintes PRIMARY KEY ont la valeur par défaut CLUSTERED et les contraintes UNIQUE la valeur par défaut NONCLUSTERED.  
  
 CLUSTERED peut être spécifié pour une seule contrainte dans une instruction CREATE TABLE. Si CLUSTERED est spécifié pour une contrainte UNIQUE et une contrainte PRIMARY KEY est également spécifiée, la contrainte PRIMARY KEY a la valeur par défaut NONCLUSTERED.  
  
 L'exemple suivant montre comment utiliser NONCLUSTERED dans une table sur disque :  
  
```  
CREATE TABLE t1 ( c1 int, INDEX ix_1 NONCLUSTERED (c1))   
CREATE TABLE t2( c1 int INDEX ix_1 NONCLUSTERED (c1))   
CREATE TABLE t3( c1 int, c2 int INDEX ix_1 NONCLUSTERED)   
CREATE TABLE t4( c1 int, c2 int, INDEX ix_1 NONCLUSTERED (c1,c2))  
```  
  
 FOREIGN KEY REFERENCES  
 Contrainte qui assure l'intégrité référentielle des données des colonnes. Avec les contraintes FOREIGN KEY, il faut que chaque valeur de la colonne existe dans la ou les colonnes référencées correspondantes de la table référencée. Les contraintes FOREIGN KEY ne peuvent référencer que des colonnes qui sont des contraintes PRIMARY KEY ou UNIQUE dans la table référencée ou des colonnes référencées dans un UNIQUE INDEX sur la table référencée. Les clés étrangères des colonnes calculées doivent également être marquées comme PERSISTED.  
  
 [ *nom_schéma***.**] *referenced_table_name*]  
 Nom de la table référencée par la contrainte FOREIGN KEY, et le schéma à laquelle elle appartient.  
  
 **(** *colonne_de_réf* [ **,**... *n* ] **)**  
 Colonne, ou liste de colonnes, provenant de la table référencée par la contrainte FOREIGN KEY.  
  
 LORS DE LA SUPPRESSION { **AUCUNE ACTION** | CASCADE | DÉFINIR NULL | PAR DÉFAUT DE SET}  
 Spécifie l'action qui se produit dans les lignes de la table créée, si ces lignes comportent une relation référentielle et si la ligne référencée est supprimée de la table parente. La valeur par défaut est NO ACTION.  
  
 NO ACTION  
 Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] déclenche une erreur et la suppression de la ligne dans la table parent est annulée.  
  
 CASCADE  
 Les lignes correspondantes sont supprimées de la table de référence pour celles supprimées de la table parent.  
  
 SET NULL  
 Toutes les valeurs qui composent la clé étrangère sont NULL si la ligne correspondante dans la table parente est supprimée. Pour que cette contrainte s'applique, les colonnes clés étrangères doivent pouvoir cependant être définies sur NULL.  
  
 SET DEFAULT  
 Toutes les valeurs qui composent la clé étrangère sont celles par défaut si la ligne correspondante dans la table parente est supprimée. Pour que cette contrainte s'applique, les colonnes clés étrangères doivent disposer cependant de valeur par défaut. Si une colonne peut être affectée de la valeur NULL et qu'aucune valeur par défaut n'est définie, NULL constitue alors la valeur par défaut de la colonne de façon implicite.  
  
 Ne spécifiez pas CASCADE si la table est incluse dans une publication de fusion qui utilise des enregistrements logiques. Pour plus d’informations sur les enregistrements logiques, consultez [Regrouper les modifications apportées à des lignes connexes à l’aide d’enregistrements logiques](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 ON DELETE CASCADE ne peut pas être défini si un déclencheur ON DELETE de INSTEAD OF existe déjà pour la table.  
  
 Par exemple, dans le [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données, le **ProductVendor** table possède une relation référentielle avec la **fournisseur** table. Le **ProductVendor.BusinessEntityID** références de clés étrangères le **Vendor.BusinessEntityID** clé primaire.  
  
 Si une instruction DELETE est exécutée sur une ligne dans le **fournisseur** table et qu’une action ON DELETE CASCADE est spécifiée pour **ProductVendor.BusinessEntityID**, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] vérifie pour une ou plusieurs lignes dépendantes dans la **ProductVendor** table. S’il en existe, les lignes dépendantes dans la **ProductVendor** table sont supprimés, ainsi que la ligne référencée dans la **fournisseur** table.  
  
 À l’inverse, si NO ACTION est spécifiée, la [!INCLUDE[ssDE](../../includes/ssde-md.md)] génère une erreur et annule l’action de suppression sur le **fournisseur** ligne s’il existe au moins une ligne dans le **ProductVendor** table fait référence.  
  
 MISE À JOUR { **AUCUNE ACTION** | CASCADE | DÉFINIR NULL | PAR DÉFAUT DE SET}  
 Spécifie l'action qui se produit sur les lignes de la table modifiée, si chacune de ces lignes possède une relation référentielle et que la ligne référencée correspondante est mise à jour dans la table parent. La valeur par défaut est NO ACTION.  
  
 NO ACTION  
 Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] déclenche une erreur et la mise à jour de la ligne dans la table parente est restaurée.  
  
 CASCADE  
 Les lignes correspondantes sont mises à jour dans la table de référence si la ligne de la table parent est mise à jour.  
  
 SET NULL  
 Toutes les valeurs composant la clé étrangère sont définies sur NULL si la ligne correspondante se trouvant à l'origine dans la table parent est mise à jour. Pour que cette contrainte s'applique, les colonnes clés étrangères doivent pouvoir cependant être définies sur NULL.  
  
 SET DEFAULT  
 Toutes les valeurs composant la clé étrangère sont définies sur leur valeur par défaut si la ligne correspondante se trouvant à l'origine dans la table parent est mise à jour. Pour que cette contrainte s'applique, les colonnes clés étrangères doivent disposer cependant de valeur par défaut. Si une colonne peut être affectée de la valeur NULL et qu'aucune valeur par défaut n'est définie, NULL constitue alors la valeur par défaut de la colonne de façon implicite.  
  
 Ne spécifiez pas CASCADE si la table est incluse dans une publication de fusion qui utilise des enregistrements logiques. Pour plus d’informations sur les enregistrements logiques, consultez [Regrouper les modifications apportées à des lignes connexes à l’aide d’enregistrements logiques](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 L'action ON UPDATE CASCADE, SET NULL ou SET DEFAULT ne peut pas être définie si le déclencheur ON UPDATE de l'option INSTEAD OF existe déjà dans la table en cours de modification.  
  
 Par exemple, dans le [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données, le **ProductVendor** table possède une relation référentielle avec la **fournisseur** table : **ProductVendor.BusinessEntity** références de clés étrangères le **Vendor.BusinessEntityID** clé primaire.  
  
 Si une instruction UPDATE est exécutée sur une ligne dans le **fournisseur** table et qu’une action ON UPDATE CASCADE est spécifiée pour **ProductVendor.BusinessEntityID**, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] vérifie pour une ou plusieurs lignes dépendantes dans la **ProductVendor** table. S’il en existe, les lignes dépendantes dans la **ProductVendor** table sont mises à jour, ainsi que la ligne référencée dans la **fournisseur** table.  
  
 À l’inverse, si NO ACTION est spécifiée, la [!INCLUDE[ssDE](../../includes/ssde-md.md)] génère une erreur et annule l’action de mise à jour de la **fournisseur** ligne s’il existe au moins une ligne dans le **ProductVendor** table fait référence.  
  
 CHECK  
 Contrainte qui assure l'intégrité du domaine en limitant les valeurs possibles pouvant être entrées dans une ou plusieurs colonnes. Les contraintes CHECK des colonnes calculées doivent également être marquées comme PERSISTED.  
  
 *Logical_Expression*  
 Expression logique qui retourne TRUE ou FALSE. Les types de données d'alias ne peuvent pas faire partie de l'expression.  
  
 *colonne*  
 Colonne, ou liste de colonnes, entre parenthèses, utilisée dans des contraintes de table pour indiquer les colonnes utilisées dans la définition de la contrainte.  
  
 [ **ASC** | DESC]  
 Indique l'ordre de tri de la ou des colonnes impliquées dans les contraintes de table. La valeur par défaut est ASC.  
  
 *partition_scheme_name*  
 Nom du schéma de partition qui définit les groupes de fichiers vers lesquels les partitions d'une table partitionnée seront mappées. Le schéma de partition doit exister dans la base de données.  
  
 [ *partition_column_name***.** ]  
 Désigne la colonne selon laquelle une table partitionnée sera partitionnée. La colonne doit correspondre que spécifié dans la partition de fonction qui *partition_scheme_name* en termes de précision, la longueur et type de données. Une colonne calculée qui participe à une fonction de partition doit être explicitement marquée comme PERSISTED.  
  
> [!IMPORTANT]  
>  Nous vous conseillons de spécifier NOT NULL sur la colonne de partitionnement des tables partitionnées et également des tables non partitionnées qui sont sources ou cibles d'opérations ALTER TABLE...SWITCH. Vous êtes ainsi certain que les contraintes CHECK sur les colonnes de partitionnement ne doivent pas rechercher la présence de valeurs Null.  
  
 FILLFACTOR  **=**  *facteur de remplissage*  
 Spécifie le remplissage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] des pages d’index qui est utilisé pour stocker les données d’index. Spécifié par l’utilisateur *fillfactor* valeurs peuvent être comprise entre 1 et 100. Si aucune valeur n'est spécifiée, la valeur par défaut est 0. Les taux de remplissage 0 et 100 sont identiques en tous points.  
  
> [!IMPORTANT]  
>  Documentation WITH FILLFACTOR = *fillfactor* que la seule option d’index qui s’applique aux contraintes PRIMARY KEY ou UNIQUE est conservée pour compatibilité descendante, mais il ne sera plus indiquée ainsi dans les futures mises à jour.  
  
 *nom_jeu_colonnes* XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
 Représente le nom du jeu de colonnes. Un jeu de colonnes est une représentation XML non typée qui combine toutes les colonnes éparses d'une table dans une sortie structurée. Pour plus d’informations sur les jeux de colonnes, consultez [Utiliser des jeux de colonnes](../../relational-databases/tables/use-column-sets.md).  
  
 PERIOD FOR SYSTEM_TIME (*system_start_time_column_name* , *system_end_time_column_name* )  
   
**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Spécifie les noms des colonnes que le système utilisera pour enregistrer la période pour laquelle un enregistrement est valide. Utilisez cet argument avec le généré toujours en tant que ligne {Démarrer | FIN} et avec SYSTEM_VERSIONING = sur les arguments pour activer le contrôle de version système sur une table. Pour plus d’informations, voir [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
 COMPRESSION_DELAY  
   
**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Pour une mémoire optimisée, délai Spécifie le nombre minimal de minutes pendant lesquelles une ligne doit rester dans la table, sans le modifier, avant qu’il soit éligible pour la compression dans l’index columnstore. SQL Server sélectionne des lignes spécifiques à compresser en fonction de leur heure de la dernière mise à jour. Par exemple, si vous modifiez des lignes fréquemment pendant une période de deux heures de temps, vous pouvez définir COMPRESSION_DELAY = 120 Minutes pour vérifier les mises à jour sont terminées avant que SQL Server compresse la ligne.  
  
 Pour une table basée sur disque, délai Spécifie le nombre minimal de minutes pendant lesquelles qu'un rowgroup delta à l’état CLOSED doit rester dans le rowgroup delta avant que SQL Server peut compresser dans le rowgroup compressé. Étant donné que les tables sur disque ne suivre insérer et mettre à jour heures sur des lignes individuelles, SQL Server s’applique le délai d’attente pour les groupes de lignes delta à l’état CLOSED.  
  
 La valeur par défaut est 0 minute.  
  
 Pour savoir à quel moment utiliser COMPRESSION_DELAY, consultez [prise en main Columnstore pour les analytique opérationnelle en temps réel](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
  
 \<table_option > :: = Spécifie une ou plusieurs options de table.  
  
 DATA_COMPRESSION  
 Spécifie l'option de compression de données pour la table, le numéro de partition ou la plage de partitions spécifiés. Les options disponibles sont les suivantes :  
  
 Aucune  
 La table ou les partitions spécifiées ne sont pas compressées.  
  
 ROW  
 La table ou les partitions spécifiées sont compressées au moyen de la compression de ligne.  
  
 PAGE  
 La table ou les partitions spécifiées sont compressées au moyen de la compression de page.  
  
 COLUMNSTORE  
   
  
**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 S'applique uniquement aux index columnstore, y compris aux index columnstore non cluster et cluster. COLUMNSTORE spécifie pour compresser avec la compression de columnstore plus performant. Il s’agit du choix par défaut.  
  
 COLUMNSTORE_ARCHIVE  
   
  
**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 S'applique uniquement aux index columnstore, y compris aux index columnstore non cluster et cluster. COLUMNSTORE_ARCHIVE compressera davantage la table ou la partition à une taille plus petite. Peut être utilisé pour l'archivage, ou d'autres situations qui nécessitent moins de stockage et supportent plus de temps pour le stockage et la récupération.  
  
 Pour plus d’informations sur la compression, consultez [la Compression des données](../../relational-databases/data-compression/data-compression.md).  
  
 SUR LES PARTITIONS **(** { `<partition_number_expression>` | [ **,**... *n* ] **)**  
 Spécifie les partitions auxquelles le paramètre DATA_COMPRESSION s'applique. Si la table n'est pas partitionnée, l'argument ON PARTITIONS génère une erreur. Si la clause ON PARTITIONS n'est pas fournie, l'option DATA_COMPRESSION s'applique à toutes les partitions d'une table partitionnée.  
  
 *partition_number_expression* peut être spécifié comme suit :  
  
-   Spécifiez le numéro de partition d'une partition, par exemple : ON PARTITIONS (2).  
  
-   Spécifiez des numéros de partition pour plusieurs partitions individuelles séparées par des virgules, par exemple : ON PARTITIONS (1, 5).  
  
-   Spécifiez à la fois des plages et des partitions individuelles, par exemple : ON PARTITIONS (2, 4, 6 TO 8).  
  
 `<range>`peut être spécifié en tant que numéros de partitions séparés par le mot TO, par exemple : ON PARTITIONS (6 TO 8).  
  
 Pour définir des types différents de compression de données pour des partitions différentes, spécifiez plusieurs fois l'option DATA_COMPRESSION, par exemple :  
  
```  
WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
)  
```  
  
 \<index_option > :: =  
 Spécifie une ou plusieurs options d'index. Pour obtenir une description complète de ces options, consultez [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
 PAD_INDEX = {ON | **OFF** }  
 Lorsque ON est spécifié, le pourcentage d'espace disponible spécifié par FILLFACTOR est appliqué aux pages de niveau intermédiaire de l'index. Lorsque OFF ou une valeur FILLFACTOR n'est pas spécifié, les pages de niveau intermédiaire de l'index sont presque entièrement remplies, ce qui laisse un espace libre suffisant pour prendre en charge au moins une ligne de la taille maximale permise par l'index, en prenant en compte l'ensemble de clés sur les pages intermédiaires. La valeur par défaut est OFF.  
  
 Facteur de remplissage  **=**  *facteur de remplissage*  
 Spécifie un pourcentage indiquant le taux de remplissage appliqué par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] au niveau feuille de chaque page d'index lors de la création ou de la modification de l'index. *facteur de remplissage* doit être un entier compris entre 1 et 100. La valeur par défaut est 0. Les taux de remplissage 0 et 100 sont identiques en tous points.  
  
 IGNORE_DUP_KEY = {ON | **OFF** }  
 Spécifie la réponse d'erreur lorsqu'une opération d'insertion essaie d'insérer des valeurs de clés en double dans un index unique. L'option IGNORE_DUP_KEY s'applique uniquement aux opérations d'insertion après la création ou la régénération de l'index. L’option n’a aucun effet lors de l’exécution [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md), [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md), ou [mise à jour](../../t-sql/queries/update-transact-sql.md). La valeur par défaut est OFF.  
  
 ON  
 Un message d'avertissement s'affichera lorsque des valeurs de clé en double sont insérées dans un index unique. Seules les lignes qui violent la contrainte d'unicité échouent.  
  
 OFF  
 Un message d'erreur s'affichera lorsque des valeurs de clé en double sont insérées dans un index unique. L'intégralité de l'opération INSERT sera restaurée.  
  
 IGNORE_DUP_KEY ne peut pas être activé (ON) dans le cas d'index créés sur une vue, d'index non uniques, d'index XML, d'index spatiaux et d'index filtrés.  
  
 Pour afficher IGNORE_DUP_KEY, utilisez [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Dans la syntaxe de compatibilité descendante, WITH IGNORE_DUP_KEY est équivalent à WITH IGNORE_DUP_KEY = ON.  
  
 STATISTICS_NORECOMPUTE  **=**  {ON | **OFF** }  
 Lorsque la valeur spécifiée est ON, les statistiques d'index périmées ne sont pas recalculées automatiquement. Lorsque la valeur spécifiée est OFF, la mise à jour automatique des statistiques est activée. La valeur par défaut est OFF.  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** | {OFF}  
 Si la valeur est ON, les verrous de ligne sont autorisés lorsque vous accédez à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] détermine le moment où les verrous de ligne sont utilisés. Si la valeur est OFF, les verrous de ligne ne sont pas utilisés. La valeur par défaut est ON.  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** | {OFF}  
 Si la valeur est ON, les verrous de page sont autorisés lorsque vous accédez à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] détermine le moment où les verrous de page sont utilisés. Si la valeur est OFF, les verrous de page ne sont pas utilisés. La valeur par défaut est ON.  
  
 FILETABLE_DIRECTORY = *directory_name*  
   
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Spécifie le nom de répertoire FileTable de compatible avec windows. Ce nom doit être unique parmi tous les noms de répertoire FileTable de la base de données. La comparaison d'unicité n'est pas sensible à la casse, indépendamment des paramètres de classement. Si cette valeur n'est pas spécifiée, le nom de la table de fichiers est utilisé.  
  
 FILETABLE_COLLATE_FILENAME = { *collation_name* | database_default}  
   
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Spécifie le nom du classement à appliquer à la colonne **Name** du FileTable. Le classement ne doit pas être sensible à la casse pour des raisons de conformité à la sémantique d'attribution des noms de fichiers Windows. Si cette valeur n'est pas spécifiée, le classement par défaut de la base de données est utilisé. Si le classement par défaut de la base de données respecte la casse, une erreur est générée et l'opération CREATE TABLE échoue.  
  
 *collation_name*  
 Nom d'un classement non sensible à la casse.  
  
 database_default  
 Spécifie que le classement par défaut de la base de données doit être utilisé. Ce classement ne doit pas être sensible à la casse.  
  
 FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME = *constraint_name*  
   
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Spécifie le nom à utiliser pour la contrainte de clé primaire qui est créée automatiquement sur le FileTable. Si cette valeur n'est pas spécifiée, le système génère un nom pour la contrainte.  
  
 FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME = *constraint_name*  
   
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Spécifie le nom à utiliser pour la contrainte unique est créée automatiquement sur le **stream_id** colonne du FileTable. Si cette valeur n'est pas spécifiée, le système génère un nom pour la contrainte.  
  
 FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME = *constraint_name*  
   
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Spécifie le nom à utiliser pour la contrainte unique est créée automatiquement sur le **parent_path_locator** et **nom** colonnes dans le FileTable. Si cette valeur n'est pas spécifiée, le système génère un nom pour la contrainte.  
  
 SYSTEM_VERSIONING  **=**  ON [(HISTORY_TABLE  **=**  *nom_schéma* .  *nom_table_historique* [, DATA_CONSISTENCY_CHECK  **=**  { **ON** | {OFF}])]  
   
  
**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].   
  
 Active le contrôle de version de système de la table si le type de données, les contraintes de possibilité de valeur null et les spécifications de contrainte de clé primaire sont remplies. Si le **HISTORY_TABLE** argument n’est pas utilisé, le système génère une nouvelle table d’historique qui correspondent au schéma de la table actuelle dans le même groupe de fichiers en tant que la table actuelle, en créant un lien entre les deux tables et permet à l’enregistrement de l’historique de chaque enregistrement dans la table actuelle dans la table d’historique. Le nom de cette table d’historique sera `MSSQL_TemporalHistoryFor<primary_table_object_id>`. Par défaut, la table d’historique est **PAGE** compressée. Si l’argument HISTORY_TABLE est utilisé pour créer un lien vers et à utiliser une table d’historique existante, le lien est créé entre la table actuelle et la table spécifiée. Si la table actuelle est partitionnée, la table d’historique est créée sur le groupe de fichiers par défaut car la configuration du partitionnement n’est pas répliquée automatiquement de la table actuelle dans la table d’historique. Si le nom d’une table d’historique est spécifié lors de sa création, vous devez spécifier le nom du schéma et de la table. Lorsque vous créez un lien vers une table de l’historique existante, vous pouvez choisir d’effectuer une vérification de cohérence des données. Cette vérification de cohérence des données garantit que les enregistrements existants ne se chevauchent pas. La vérification de cohérence des données est effectuée par défaut. Utilisez cet argument avec l’instruction PERIOD FOR SYSTEM_TIME et généré toujours en tant que ligne {Démarrer | Arguments de fin} pour activer le contrôle de version système sur une table. Pour plus d’informations, voir [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
 REMOTE_DATA_ARCHIVE = {ON [( *table_stretch_options* [,... n])] | OFF (MIGRATION_STATE = EN PAUSE)}  
   
  
**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Crée la nouvelle table avec Stretch Database activée ou désactivée. Pour plus d'informations, consultez [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
 **L’activation de Stretch Database pour une table**  
  
 Lorsque vous activez Stretch pour une table en spécifiant `ON`, vous pouvez éventuellement spécifier `MIGRATION_STATE = OUTBOUND` pour commencer à migrer les données immédiatement, ou `MIGRATION_STATE = PAUSED` pour reporter la migration des données. La valeur par défaut est `MIGRATION_STATE = OUTBOUND`. Pour plus d’informations sur l’activation de Stretch pour une table, consultez [Enable Stretch Database pour une table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
 **Conditions préalables**. Avant d’activer Stretch pour une table, vous devez activer l’extension sur le serveur et sur la base de données. Pour plus d'informations, consultez [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 **Les autorisations**. L’activation de Stretch pour une base de données ou une table nécessite les autorisations db_owner. L’activation de Stretch pour une table requiert également l’autorisation ALTER sur la table.  
  
 [FILTER_PREDICATE = {null | *prédicat* }]  
   
  
**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie éventuellement un prédicat de filtre pour sélectionner les lignes à migrer à partir d’une table qui contient les données historiques et actuelles. Le prédicat doit appeler une fonction table inline déterministe. Pour plus d’informations, consultez [Enable Stretch Database pour une table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) et [sélectionner les lignes à migrer à l’aide d’une fonction de filtre](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md). 
   
> [!IMPORTANT]  
>  Si vous fournissez un prédicat de filtre qui fonctionne mal, la migration des données fonctionne mal également. Stretch Database applique le prédicat de filtre à la table à l’aide de l’opérateur CROSS APPLY.  
  
 Si vous ne spécifiez aucun prédicat de filtre, la table entière est migrée.  
  
 Lorsque vous spécifiez un prédicat de filtre, vous devez également spécifier *MIGRATION_STATE*.  
  
 MIGRATION_STATE = {SORTANTS |  ENTRANTS | SUSPENDU}  
   
  
**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]et SQL Azure. 
  
-   Spécifiez `OUTBOUND` pour migrer des données à partir de SQL Server vers Azure.  
  
-   Spécifiez `INBOUND` distant de copier les données de la table d’Azure sauvegarder vers SQL Server et pour désactiver Stretch pour la table. Pour plus d’informations, consultez [Désactiver Stretch Database et récupérer les données distantes](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).  
  
     Cette opération entraîne des coûts de transfert de données et ne peut pas être annulée.  
  
-   Spécifiez `PAUSED` pour interrompre ou reporter la migration des données. Pour plus d’informations, consultez [suspendre et reprendre la migration des données &#40; Stretch Database &#41; ](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
 MEMORY_OPTIMIZED  
   
  
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 La valeur ON indique que la table est optimisée en mémoire. Tables optimisées en mémoire font partie de la fonctionnalité OLTP en mémoire, qui sert à optimisé les performances de traitement des transactions. Prise en main OLTP en mémoire voir [démarrage rapide 1 : Technologies de l’OLTP en mémoire plus rapidement les performances Transact-SQL](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md). Pour plus d’informations sur les tables mémoire optimisées, consultez [Tables optimisées en mémoire](../../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 La valeur par défaut OFF indique que la table est basée sur disque.  
  
 DURABILITY  
   
  
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].   
  
 La valeur de SCHEMA_AND_DATA indique que la table est durable, ce qui signifie que les modifications sont rendues persistantes sur disque et survivent au redémarrage ou basculement.  SCHEMA_AND_DATA est la valeur par défaut.  
  
 La valeur de SCHEMA_ONLY indique que la table est une table non durable. Le schéma de table est conservé, mais les mises à jour de données ne sont pas conservées lors d’un redémarrage ou basculement de la base de données. DURABILITÉ = SCHEMA_ONLY est uniquement autorisé avec MEMORY_OPTIMIZED = ON.  
  
> [!WARNING]  
>  Lorsqu’une table est créée avec **durabilité = SCHEMA_ONLY**, et **READ_COMMITTED_SNAPSHOT** est modifié par la suite à l’aide de **ALTER DATABASE**, données de la table seront perdues.  
  
 BUCKET_COUNT  
   
  
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. 
  
 Indique le nombre de compartiments qui doivent être créés dans l'index de hachage. La valeur maximale de BUCKET_COUNT dans les index de hachage est de 1 073 741 824. Pour plus d’informations sur le nombre de compartiments, consultez [index des Tables mémoire optimisées](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
 Bucket_count est un argument obligatoire.  
  
 INDEX  
   
  
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. 
  
Index de table et de colonne peuvent être spécifiés en tant que partie de l’instruction CREATE TABLE. Pour plus d’informations sur l’ajout et suppression d’index sur les tables mémoire optimisées, consultez : [des Tables mémoire optimisées](../../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md)
  
 HASH  
   
  
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. 
  
 Indique qu'un index HASH est créé.  
  
 Les index de hachage sont pris en charge uniquement sur les tables mémoire optimisées.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur le nombre de tables autorisés, colonnes, contraintes et index, consultez [spécifications des capacités maximales pour SQL Server](../../sql-server/maximum-capacity-specifications-for-sql-server.md).  
  
 L'espace est généralement alloué aux tables et aux index par incréments d'une valeur d'extension à la fois. Lorsque l’option SET MIXED_PAGE_ALLOCATION d’ALTER DATABASE a la valeur TRUE, ou toujours antérieures à [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], lorsqu’une table ou un index est créé, les pages sont allouées à partir d’extensions mixtes jusqu'à ce qu’il ait suffisamment de pages pour remplir une extension uniforme. Quand il y a assez de pages pour remplir une extension uniforme, une autre extension est allouée chaque fois que l'extension active est pleine. Pour un rapport sur la quantité d’espace allouée et utilisée par une table, exécutez **sp_spaceused**.  
  
 Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne garantit pas l'application de l'ordre dans lequel des contraintes DEFAULT, IDENTITY, ROWGUIDCOL, ou des contraintes de colonne, sont spécifiées dans une définition de colonne.  
  
 Lors de la création d'une table, l'option QUOTED IDENTIFIER est toujours stockée avec la valeur ON dans les métadonnées de la table, même si elle a la valeur OFF au moment de sa création.  
  
## <a name="temporary-tables"></a>Tables temporaires  
 Vous pouvez créer des tables temporaires locales et globales. Les tables temporaires locales ne peuvent être vues que dans la session active ; les tables temporaires globales sont accessibles dans toutes les sessions. Les tables temporaires ne peuvent pas être partitionnées.  
  
 Faites précéder les noms de table temporaire locale avec le signe dièse (#*table_name*) et faites précéder les noms de table temporaire globale avec deux signes dièse (##*table_name*).  
  
 Instructions SQL font référence à la table temporaire à l’aide de la valeur spécifiée pour *table_name* dans l’instruction CREATE TABLE, pour l’exemple ### :  
  
```  
CREATE TABLE #MyTempTable (cola INT PRIMARY KEY);  
  
INSERT INTO #MyTempTable VALUES (1);  
```  
  
 Si plusieurs tables temporaires sont créées dans un lot ou une seule procédure stockée, elles doivent porter des noms différents.  
  
 Si vous créez une table temporaire locale dans une procédure stockée ou dans une application qui peut être exécutée en même temps par plusieurs utilisateurs, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit être capable de distinguer les tables créées par les différents utilisateurs. Cela est effectué en interne par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] en ajoutant de manière interne un suffixe numérique à chaque nom de table temporaire locale. Le nom complet d’une table temporaire stockés dans le **sysobjects** table **tempdb** est constitué du nom de table spécifié dans l’instruction CREATE TABLE et le suffixe numérique généré par le système. Pour permettre le suffixe, *table_name* spécifié pour un nom temporaire local ne peut pas dépasser 116 caractères.  
  
 Les tables temporaires sont automatiquement supprimées lorsqu'elles passent hors de portée, sauf si elles sont supprimées explicitement à l'aide de DROP TABLE :  
  
-   Une table temporaire locale créée dans une procédure stockée est supprimée automatiquement lorsque la procédure stockée est terminée. La table peut être référencée par des procédures stockées imbriquées exécutées par la procédure stockée qui a créé la table. La table ne peut pas être référencée par le processus qui a appelé la procédure stockée ayant créé la table.  
  
-   Toutes les autres tables temporaires locales sont supprimées automatiquement à la fin de la session active.  
  
-   Les tables temporaires globales sont supprimées automatiquement lorsque la session qui a créé la table se termine, et que toutes les autres tâches n'y font plus référence. L'association entre une tâche et une table n'est assurée que pendant la durée d'une seule instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. Cela signifie qu'une table temporaire globale est supprimée à la fin de la dernière instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui faisait activement référence à la table lorsque la session de création s'est terminée.  
  
 Une table temporaire locale créée au sein d'une procédure stockée ou d'un déclencheur peut avoir le même nom qu'une table temporaire créée avant l'appel de la procédure stockée ou du déclencheur. Cependant, si une requête fait référence à une table temporaire et si deux tables temporaires portent ce nom, la table par rapport à laquelle la requête est résolue n'est pas définie. Les procédures stockées imbriquées peuvent également créer des tables temporaires portant le même nom qu'une table temporaire créée par la procédure stockée qui l'a appelée. Cependant, pour que les modifications résolvent la table créée par la procédure imbriquée, la table doit avoir la même structure, avec les mêmes noms de colonnes, que la table créée dans la procédure d'appel. Cela est illustré par l'exemple suivant.  
  
```  
CREATE PROCEDURE dbo.Test2  
AS  
    CREATE TABLE #t(x INT PRIMARY KEY);  
    INSERT INTO #t VALUES (2);  
    SELECT Test2Col = x FROM #t;  
GO  
  
CREATE PROCEDURE dbo.Test1  
AS  
    CREATE TABLE #t(x INT PRIMARY KEY);  
    INSERT INTO #t VALUES (1);  
    SELECT Test1Col = x FROM #t;  
EXEC Test2;  
GO  
  
CREATE TABLE #t(x INT PRIMARY KEY);  
INSERT INTO #t VALUES (99);  
GO  
  
EXEC Test1;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `(1 row(s) affected)`  
  
 `Test1Col`  
  
 `-----------`  
  
 `1`  
  
 `(1 row(s) affected)`  
  
 `Test2Col`  
  
 `-----------`  
  
 `2`  
  
 Lorsque vous créez des tables temporaires locales ou globales, la syntaxe CREATE TABLE prend en charge les définitions de contraintes à l'exception des contraintes FOREIGN KEY. Si vous spécifiez une contrainte FOREIGN KEY dans une table temporaire, l'instruction retourne un message d'avertissement précisant que la contrainte a été ignorée. La table est toujours créée mais sans les contraintes FOREIGN KEY. Les tables temporaires ne peuvent pas être référencées dans des contraintes FOREIGN KEY.  
  
 Si une table temporaire est créée avec une contrainte nommée et dans l'étendue d'une transaction définie par l'utilisateur, un seul utilisateur à la fois peut exécuter l'instruction qui crée la table temp. Par exemple, si une procédure stockée crée une table temporaire avec une contrainte nommée de clé primaire, elle ne peut pas être exécutée simultanément par plusieurs utilisateurs.  


## <a name="database-scoped-global-temporary-tables-azure-sql-database"></a>Étendue de la base de données des tables temporaires globales (de base de données SQL Azure)

Les tables temporaires globales pour SQL Server (démarrée avec ## nom de la table) sont stockées dans tempdb et partagées entre les sessions de tous les utilisateurs dans toute l’instance de SQL Server. Pour plus d’informations sur les types de tables SQL, consultez la section ci-dessus sur les Tables de créer.  

Base de données SQL Azure prend en charge les tables temporaires globales qui sont également stockées dans tempdb et étendues au niveau de la base de données.  Cela signifie que les tables temporaires globales sont partagés pour les sessions de tous les utilisateurs au sein de la même base de données SQL Azure. Sessions utilisateur à partir d’autres bases de données SQL Azure ne peut pas accéder aux tables temporaires globales.

Les tables temporaires globales pour la base de données SQL Azure suivent la même syntaxe et sémantique que SQL Server utilise pour les tables temporaires.  De même, les procédures stockées temporaires globales sont également limités au niveau de la base de données dans la base de données SQL Azure. Les tables temporaires locales (initiés avec le nom de la table #) sont également pris en charge pour la base de données SQL Azure et suivent la même syntaxe et sémantique que SQL Server utilise.  Consultez la section ci-dessus sur [Tables temporaires](#temporary-tables).  

> [!IMPORTANT]
> Cette fonctionnalité en version préliminaire publique et est disponible pour la base de données SQL Azure.
>

### <a name="troubleshooting-global-temporary-tables-for-azure-sql-db"></a>Dépannage des tables temporaires globales pour la base de données SQL Azure 

Pour le dépannage de base de données tempdb, consultez [dépannage le manque d’espace dans tempdb](https://technet.microsoft.com/library/ms176029%28v=sql.105%29.aspx?f=255&MSPPError=-2147217396). Pour accéder aux résolution des problèmes DMV dans la base de données SQL Azure, vous devez être un administrateur du serveur.
  
### <a name="permissions"></a>Permissions  

 Tout utilisateur peut créer des objets temporaires globaux. Les utilisateurs n'ont accès qu'aux objets qu'ils possèdent, sauf s'ils ont reçu des autorisations supplémentaires. .  
  
### <a name="examples"></a>Exemples 

- La session A crée une table temporaire globale ##test dans la base de données SQL Azure testdb1 et ajoute la 1 ligne

```tsql
CREATE TABLE ##test ( a int, b int);
INSERT INTO ##test values (1,1);

--Obtain object ID for temp table ##test 
SELECT OBJECT_ID('tempdb.dbo.##test') AS 'Object ID'; 

---Result
1253579504

---Obtain global temp table name for a given object ID 1253579504 in tempdb (2)
SELECT name FROM tempdb.sys.objects WHERE object_id = 1253579504

---Result
##test
```
- Session B se connecte à la base de données SQL Azure testdb1 et peut accéder à la table ##test créée par la session A

```tsql
SELECT * FROM ##test
---Results
1,1
```

- Session C se connecte à une autre base de données dans la base de données SQL Azure testdb2 et veut accéder ##test créé dans testdb1. Cette instruction select échoue en raison de l’étendue de la base de données pour les tables temporaires globales 

```tsql
SELECT * FROM ##test
---Results
Msg 208, Level 16, State 0, Line 1
Invalid object name '##test'
```

- Adressage des objets système dans la base de données SQL Azure tempdb à partir de testdb1 de base de données utilisateur en cours

```tsql
SELECT * FROM tempdb.sys.objects
SELECT * FROM tempdb.sys.columns
SELECT * FROM tempdb.sys.database_files
```



## <a name="partitioned-tables"></a>Tables partitionnées  
 Avant de créer une table partitionnée à l'aide de CREATE TABLE, vous devez d'abord créer une fonction de partition pour spécifier la manière dont la table est partitionnée. Une fonction de partition est créée à l’aide de [CREATE PARTITION FUNCTION](../../t-sql/statements/create-partition-function-transact-sql.md). Ensuite, vous devez créer un schéma de partition pour spécifier les groupes de fichiers qui contiendront les partitions indiquées par la fonction de partition. Un schéma de partition est créé à l’aide de [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md). Le placement des contraintes PRIMARY KEY ou UNIQUE pour séparer les groupes de fichiers ne peut pas être spécifié pour les tables partitionnées. Pour plus d’informations, consultez [Tables et index partitionnés](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
## <a name="primary-key-constraints"></a>Contraintes PRIMARY KEY  
  
-   Une table ne peut contenir qu'une seule contrainte PRIMARY KEY.  
  
-   L'index généré par une contrainte PRIMARY KEY ne peut avoir pour conséquence une augmentation du nombre d'index dans la table à plus de 999 index non cluster et un index cluster.  
  
-   Si vous ne spécifiez pas CLUSTERED ou NONCLUSTERED pour une contrainte PRIMARY KEY, CLUSTERED est utilisé s'il n'y a pas d'index cluster spécifiés pour les contraintes UNIQUE.  
  
-   Toutes les colonnes définies dans une contrainte PRIMARY KEY doivent avoir la valeur NOT NULL. Si vous ne spécifiez pas la possibilité ou non de valeurs NULL, toutes les colonnes participant à une contrainte PRIMARY KEY sont définies à NOT NULL.  
  
    > [!NOTE]  
    >  Pour les tables optimisées en mémoire, la colonne clé autorisant la valeur NULL est autorisée.  
  
-   Si une clé primaire est définie sur une colonne avec le type de données CLR défini par l'utilisateur, l'implémentation du type doit prendre en charge le tri binaire. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
## <a name="unique-constraints"></a>Contraintes UNIQUE  
  
-   Si vous ne spécifiez pas CLUSTERED ou NONCLUSTERED pour une contrainte UNIQUE, NONCLUSTERED est utilisé par défaut.  
  
-   Chaque contrainte UNIQUE génère un index. Le nombre de contraintes UNIQUE ne peut avoir pour conséquence une augmentation du nombre d'index dans la table à plus de 999 index non cluster et 1 index cluster.  
  
-   Si une contrainte unique est définie sur une colonne avec le type de données CLR défini par l'utilisateur, l'implémentation du type doit prendre en charge le tri binaire ou basé sur l'opérateur. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
## <a name="foreign-key-constraints"></a>Contraintes FOREIGN KEY  
  
-   Lorsqu'une valeur différente de NULL est entrée dans la colonne d'une contrainte FOREIGN KEY, la valeur doit exister dans la colonne référencée. Dans le cas contraire, le système retourne un message d'erreur signalant une violation de clé étrangère.  
  
-   Les contraintes FOREIGN KEY sont appliquées à la colonne précédente, à moins que des colonnes sources ne soient spécifiées.  
  
-   Les contraintes FOREIGN KEY ne peuvent faire référence qu'à des tables au sein de la même base de données sur le même serveur. L'intégrité référentielle inter-base de données doit être implémentée via les déclencheurs. Pour plus d’informations, consultez [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
-   Les contraintes FOREIGN KEY peuvent faire référence à une autre colonne dans la même table. On appelle habituellement ce mécanisme « auto-référence ».  
  
-   La clause REFERENCES d'une contrainte FOREIGN KEY au niveau des colonnes, ne peut lister qu'une colonne de référence. Cette colonne doit avoir le même type de données que la colonne pour laquelle la contrainte est définie.  
  
-   La clause REFERENCES d'une contrainte FOREIGN KEY de niveau table doit avoir le même nombre de colonnes de référence que le nombre de colonnes de la liste des colonnes de la contrainte. Le type de données de chaque colonne de référence doit également être identique à la colonne de référence correspondante dans la liste des colonnes.  
  
-   CASCADE, SET NULL ou SET DEFAULT ne peut pas être spécifiée si une colonne de type **timestamp** fait partie de la clé étrangère ou la clé référencée.  
  
-   Il est possible de combiner CASCADE, SET NULL, SET DEFAULT et NO ACTION pour des tables liées par des relations référentielles. Si le moteur [!INCLUDE[ssDE](../../includes/ssde-md.md)] rencontre NO ACTION, il s’interrompt et restaure les actions CASCADE, SET NULL et SET DEFAULT. Lorsqu'une instruction DELETE génère une combinaison d'actions CASCADE, SET NULL, SET DEFAULT et NO ACTION, les actions CASCADE, SET NULL et SET DEFAULT sont appliquées par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] avant toute recherche de NO ACTION.  
  
-   Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n'a pas de limite prédéfinie du nombre de contraintes FOREIGN KEY qu'une table peut contenir et qui référencent d'autres tables ou du nombre de contraintes FOREIGN KEY possédées par d'autres tables qui font référence à une table spécifique.  
  
     Cependant, le nombre réel de contraintes FOREIGN KEY qui peuvent être utilisées est limité par la configuration matérielle et par la conception de la base de données et de l'application. Nous vous recommandons de ne pas insérer plus de 253 contraintes FOREIGN KEY dans une table et qu'une même table ne soit pas référencée par plus de 253 contraintes FOREIGN KEY. La limite effective pour vous peut varier en fonction de l'application et du matériel. Prenez en compte le coût d'application des contraintes FOREIGN KEY avant de concevoir vos bases de données et applications.  
  
-   Les contraintes FOREIGN KEY ne sont pas appliquées dans les tables temporaires.  
  
-   Les contraintes FOREIGN KEY ne peuvent référencer que les colonnes dans des contraintes PRIMARY KEY ou UNIQUE dans la table référencée ou dans un index UNIQUE INDEX de la table référencée.  
  
-   Si une clé étrangère est définie sur une colonne avec le type de données CLR défini par l'utilisateur, l'implémentation du type doit prendre en charge le tri binaire. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
-   Colonnes qui participent à une relation de clé étrangère doivent être définis avec la même longueur et l’échelle.  
  
## <a name="default-definitions"></a>Définitions DEFAULT  
  
-   Une colonne ne peut avoir qu'une seule définition DEFAULT (valeur par défaut).  
  
-   Une définition DEFAULT peut contenir des valeurs constantes, des fonctions, des fonctions niladiques SQL standard ou des valeurs NULL. Le tableau suivant montre les fonctions niladiques et les valeurs qu'elles retournent pour la valeur par défaut, lors d'une instruction INSERT.  
  
    |Fonction niladique SQL-92|Valeur retournée|  
    |------------------------------|--------------------|  
    |CURRENT_TIMESTAMP|Date et heure actuelles.|  
    |CURRENT_USER|Nom de l'utilisateur effectuant une insertion.|  
    |SESSION_USER|Nom de l'utilisateur effectuant une insertion.|  
    |SYSTEM_USER|Nom de l'utilisateur effectuant une insertion.|  
    |Utilisateur|Nom de l'utilisateur effectuant une insertion.|  
  
-   *expression_constante* dans une valeur par défaut définition ne peut pas faire référence à une autre colonne dans la table, ou à d’autres tables, vues ou des procédures stockées.  
  
-   Définitions DEFAULT ne peut pas être créées sur des colonnes avec un **timestamp** type de données ou les colonnes avec une propriété d’identité.  
  
-   Les définitions DEFAULT ne peuvent pas être créées pour des colonnes qui possèdent des types de données d'alias, si ces types de données sont liés à un objet par défaut.  
  
## <a name="check-constraints"></a>Contraintes CHECK  
  
-   Une colonne peut posséder un nombre illimité de contraintes CHECK et la condition peut inclure plusieurs expressions logiques combinées par AND et OR. S'il existe plusieurs contraintes CHECK pour une même colonne, elles sont validées dans l'ordre de leur création.  
  
-   La condition de recherche doit correspondre à une expression booléenne et ne peut pas faire référence à une autre table.  
  
-   Une contrainte CHECK de niveau colonne ne peut faire référence qu'à la colonne contenant la contrainte, et une contrainte CHECK de niveau table ne peut faire référence qu'aux colonnes d'une même table.  
  
     Les contraintes CHECK et les règles servent toutes les deux à valider les données lors des instructions INSERT et UPDATE.  
  
-   Quand il existe une règle et une ou plusieurs contraintes CHECK pour une colonne, toutes les restrictions sont évaluées.  
  
-   Contraintes de validation ne peut pas être définies sur **texte**, **ntext**, ou **image** colonnes.  
  
## <a name="additional-constraint-information"></a>Informations supplémentaires sur les contraintes  
  
-   Un index créé pour une contrainte ne peut pas être supprimé en utilisant DROP INDEX ; la contrainte doit être supprimée à l'aide de ALTER TABLE. Un index créé pour une contrainte et utilisé par elle peut être recréé en utilisant ALTER INDEX...REBUILD. Pour plus d’informations, consultez [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Les noms de contrainte doivent respecter les règles pour [identificateurs](../../relational-databases/databases/database-identifiers.md), sauf que le nom ne peut pas commencer par un signe dièse (#). Si *constraint_name* est ne pas fourni, un nom généré par le système est affecté à la contrainte. Le nom de la contrainte apparaît dans tous les messages d'erreur relatifs aux violations de contraintes.  
  
-   Lorsqu'une contrainte est violée dans une instruction INSERT, UPDATE ou DELETE, l'instruction est terminée. Cependant, lorsque SET XACT_ABORT a la valeur OFF, la transaction, si l'instruction fait partie d'une transaction explicite, continue à être traitée. Lorsque SET XACT_ABORT a pour valeur ON, toute la transaction est restaurée. Vous pouvez également utiliser l’instruction ROLLBACK TRANSACTION avec la définition de la transaction en vérifiant le @@ERROR fonction système.  
  
-   Si ALLOW_ROW_LOCKS = ON et ALLOW_PAGE_LOCK = ON, les verrous de ligne, de page et de table sont autorisés lorsque vous accédez à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] choisit le verrou approprié et peut promouvoir un verrou de ligne ou de page en verrou de table. Si ALLOW_ROW_LOCKS = OFF et ALLOW_PAGE_LOCK = OFF, seul un verrou au niveau des tables est autorisé si vous accédez à l'index.  
  
-   Si une table contient des contraintes FOREIGN KEY ou CHECK, et des déclencheurs, les conditions de la contrainte sont évaluées avant l'exécution du déclencheur.  
  
 Pour un rapport sur une table et ses colonnes, utilisez **sp_help** ou **sp_helpconstraint**. Pour renommer une table, utilisez **sp_rename**. Pour un rapport sur les vues et les procédures stockées qui dépendent d’une table, utilisez [sys.dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md) et [sys.dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md).  
  
## <a name="nullability-rules-within-a-table-definition"></a>Règles des possibilités de valeurs Null dans une définition de table  
 La possibilité de valeurs Null pour une colonne détermine si cette colonne peut accepter une valeur Null (NULL) comme données dans la colonne. La valeur NULL n'est pas équivalente à la valeur zéro ou à un blanc : cela signifie qu'il n'y a pas eu d'entrée dans la colonne ou que la valeur NULL explicite a été spécifiée. Cela implique généralement que la valeur est inconnue ou non applicable.  
  
 Lorsque vous créez ou modifiez une table à l'aide des instructions CREATE TABLE ou ALTER TABLE, les paramètres de la base de données et de la session influencent et éventuellement modifient la possibilité de valeur Null pour le type de données utilisé dans une définition de colonne. Il est recommandé de toujours définir explicitement une colonne comme NULL ou NOT NULL ou, si vous utilisez un type de données défini par l'utilisateur, d'autoriser la colonne à utiliser la possibilité de valeur NULL par défaut pour ce type de données. Les colonnes éparses doivent toujours autoriser les valeurs NULL.  
  
 Lorsque vous ne l'avez pas spécifiée explicitement, la possibilité de valeurs Null pour les colonnes respecte les règles récapitulées dans le tableau suivant :  
  
|Type de données de la colonne|Règle|  
|----------------------|----------|  
|Type de données d'alias|Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise la possibilité de valeurs Null spécifiée lors de la création du type de données. Pour déterminer la possibilité de valeur NULL par défaut du type de données, utilisez **sp_help**.|  
|type CLR défini par l'utilisateur|La possibilité de valeur NULL est déterminée en fonction de la définition de la colonne.|  
|Type de données fourni par le système|Si le type de données fourni par le système ne possède qu'une option, il a priorité. **horodatage** types de données doivent être non NULL. Lorsque les paramètres de session ont pour valeur ON en utilisant SET :<br />**ANSI_NULL_DFLT_ON** = ON, NULL est affecté.  <br />**SET ANSI_NULL_DFLT_OFF** = ON, NOT NULL est affecté.<br /><br /> Lorsque les paramètres de base de données sont configurés en utilisant ALTER DATABASE :<br />**ANSI_NULL_DEFAULT_ON** = ON, NULL est affecté.  <br />**ANSI_NULL_DEFAULT_OFF** = ON, NOT NULL est affecté.<br /><br /> Pour afficher le paramètre de base de données pour ANSI_NULL_DEFAULT, utilisez le **sys.databases** affichage catalogue|  
  
 Si aucune des options ANSI_NULL_DFLT n'est définie pour la session et si la base de données est définie avec les valeurs par défaut (ANSI_NULL_DEFAULT étant OFF), la valeur par défaut, NOT NULL, est affectée.  
  
 La possibilité de valeurs NULL dans les colonnes calculées est déterminée automatiquement par le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Pour rechercher les valeurs NULL de ce type de colonne, utilisez la fonction COLUMNPROPERTY avec la **AllowsNull** propriété.  
  
> [!NOTE]  
>  Que ce soit pour le pilote ODBC de SQL Server ou pour le fournisseur Microsoft OLE DB de SQL Server, ANSI_NULL_DFLT_ON a par défaut la valeur ON. Les utilisateurs ODBC et OLE DB peuvent réaliser cette configuration dans les sources de données ODBC ou à l'aide d'attributs ou de propriétés de connexion définies par l'application.  
  
## <a name="data-compression"></a>Data Compression  
 Les tables système ne peuvent pas être activées pour la compression. Lorsque vous créez une table ou un index, la compression de données est définie sur NONE, sauf indication contraire. Si vous spécifiez une liste de partitions ou une partition hors limites, une erreur est générée. Pour plus d’informations sur la compression de données, consultez [Compression des données](../../relational-databases/data-compression/data-compression.md).  
  
 Pour évaluer la façon dont la modification de l’état de compression affecte une table, un index ou une partition, utilisez la procédure stockée [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) .  
  
## <a name="permissions"></a>Permissions  
 Nécessite une autorisation CREATE TABLE dans la base de données et une autorisation ALTER pour le schéma dans lequel la table a été créée.  
  
 Si des colonnes dans l'instruction CREATE TABLE sont définies avec le type de données CLR défini par l'utilisateur, la propriété du type ou une autorisation REFERENCES est nécessaire.  
  
 Si des colonnes dans l'instruction CREATE TABLE sont associées à une collection de schémas XML, la propriété de la collection de schémas XML ou une autorisation REFERENCES pour le type est nécessaire.  
  
 Tout utilisateur peut créer des tables temporaires dans tempdb.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-create-a-primary-key-constraint-on-a-column"></a>A. Créer une contrainte PRIMARY KEY dans une colonne  
 L'exemple suivant affiche la définition de colonne pour une contrainte PRIMARY KEY avec un index cluster sur la colonne `EmployeeID` de la table `Employee`. Étant donné que le nom de la contrainte n'est pas spécifié, le système en fournit un.  
  
```  
CREATE TABLE dbo.Employee (EmployeeID int  
PRIMARY KEY CLUSTERED);  
```  
  
### <a name="b-using-foreign-key-constraints"></a>B. Utilisation des contraintes FOREIGN KEY  
 Une contrainte FOREIGN KEY sert à référencer une autre table. Les clés étrangères peuvent être des clés à colonne unique ou sur plusieurs colonnes. Cet exemple montre une contrainte FOREIGN KEY à colonne unique dans la table `SalesOrderHeader` qui fait référence à la table `SalesPerson`. Seule la clause REFERENCES est obligatoire pour une contrainte FOREIGN KEY à colonne unique.  
  
```  
SalesPersonID int NULL  
REFERENCES SalesPerson(SalesPersonID)  
```  
  
 Vous pouvez également utiliser de manière explicite la clause FOREIGN KEY et redéterminer l'attribut de la colonne. Notez que le nom de la colonne ne doit pas nécessairement être le même dans les deux tables.  
  
```  
FOREIGN KEY (SalesPersonID) REFERENCES SalesPerson(SalesPersonID)  
```  
  
 Les contraintes de clés sur plusieurs colonnes sont créées comme des contraintes de table. Dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], la table `SpecialOfferProduct` inclut une clause PRIMARY KEY sur plusieurs colonnes. L'exemple suivant montre comment faire référence à cette clé à partir d'une autre table ; un nom de contrainte explicite n'est pas obligatoire.  
  
```  
CONSTRAINT FK_SpecialOfferProduct_SalesOrderDetail FOREIGN KEY  
 (ProductID, SpecialOfferID)  
REFERENCES SpecialOfferProduct (ProductID, SpecialOfferID)  
```  
  
### <a name="c-using-unique-constraints"></a>C. Utilisation des contraintes UNIQUE  
 Les contraintes UNIQUE servent à garantir l'unicité dans les colonnes qui n'ont pas de clés primaires. L'exemple suivant applique la restriction suivant laquelle la colonne `Name` de la table `Product` doit être unique.  
  
```  
Name nvarchar(100) NOT NULL  
UNIQUE NONCLUSTERED  
```  
  
### <a name="d-using-default-definitions"></a>D. Utilisation des définitions DEFAULT  
 Les valeurs par défaut fournissent une valeur (avec les instructions INSERT et UPDATE) lorsqu'aucune valeur n'est fournie. Par exemple, la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] peut inclure une table de correspondance répertoriant les différents emplois que les employés peuvent occuper dans la société. Sous une colonne décrivant chaque emploi, une chaîne de caractères par défaut peut fournir une description lorsqu'aucune description réelle n'est entrée explicitement.  
  
```  
DEFAULT 'New Position - title not formalized yet'  
```  
  
 Outre des constantes, les définitions DEFAULT peuvent inclure des fonctions. Utilisez l'exemple suivant pour obtenir la date actuelle d'une entrée.  
  
```  
DEFAULT (getdate())  
```  
  
 Une fonction niladique peut également améliorer l'intégrité des données. Afin de garder une trace de l'utilisateur qui a inséré une ligne, utilisez la fonction niladique pour USER. N'entourez pas les fonctions niladiques de parenthèses.  
  
```  
DEFAULT USER  
```  
  
### <a name="e-using-check-constraints"></a>E. Utilisation des contraintes CHECK  
 L'exemple suivant affiche une restriction appliquée aux valeurs entrées dans la colonne `CreditRating` de la table `Vendor`. La contrainte n'a pas de nom.  
  
```  
CHECK (CreditRating >= 1 and CreditRating <= 5)  
```  
  
 Cet exemple montre une contrainte nommée avec un modèle de restriction pour les données caractères entrées dans une colonne d'une table.  
  
```  
CONSTRAINT CK_emp_id CHECK (emp_id LIKE   
'[A-Z][A-Z][A-Z][1-9][0-9][0-9][0-9][0-9][FM]'   
OR emp_id LIKE '[A-Z]-[A-Z][1-9][0-9][0-9][0-9][0-9][FM]')  
```  
  
 Cet exemple spécifie que les valeurs doivent figurer dans une liste spécifique ou suivre un modèle donné.  
  
```  
CHECK (emp_id IN ('1389', '0736', '0877', '1622', '1756')  
OR emp_id LIKE '99[0-9][0-9]')  
```  
  
### <a name="f-showing-the-complete-table-definition"></a>F. Affichage des définitions de tables complètes  
 Cet exemple montre des définitions complètes de tables avec toutes les définitions de contraintes pour la table `PurchaseOrderDetail` créée dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Notez que pour exécuter l'exemple, le schéma de table est modifié en `dbo`.  
  
```  
CREATE TABLE dbo.PurchaseOrderDetail  
(  
    PurchaseOrderID int NOT NULL  
        REFERENCES Purchasing.PurchaseOrderHeader(PurchaseOrderID),  
    LineNumber smallint NOT NULL,  
    ProductID int NULL   
        REFERENCES Production.Product(ProductID),  
    UnitPrice money NULL,  
    OrderQty smallint NULL,  
    ReceivedQty float NULL,  
    RejectedQty float NULL,  
    DueDate datetime NULL,  
    rowguid uniqueidentifier ROWGUIDCOL  NOT NULL  
        CONSTRAINT DF_PurchaseOrderDetail_rowguid DEFAULT (newid()),  
    ModifiedDate datetime NOT NULL   
        CONSTRAINT DF_PurchaseOrderDetail_ModifiedDate DEFAULT (getdate()),  
    LineTotal  AS ((UnitPrice*OrderQty)),  
    StockedQty  AS ((ReceivedQty-RejectedQty)),  
    CONSTRAINT PK_PurchaseOrderDetail_PurchaseOrderID_LineNumber  
               PRIMARY KEY CLUSTERED (PurchaseOrderID, LineNumber)  
               WITH (IGNORE_DUP_KEY = OFF)  
)   
ON PRIMARY;  
```  
  
### <a name="g-creating-a-table-with-an-xml-column-typed-to-an-xml-schema-collection"></a>G. Création d'une table avec une colonne XML de type collection de schémas XML  
 L'exemple suivant crée une table avec une colonne `xml` de type collection de schémas XML `HRResumeSchemaCollection`. Le `DOCUMENT` mot clé spécifie que chaque instance de la `xml` de type de données dans *column_name* peut contenir qu’un seul élément de niveau supérieur.  
  
```  
CREATE TABLE HumanResources.EmployeeResumes   
   (LName nvarchar(25), FName nvarchar(25),   
    Resume xml( DOCUMENT HumanResources.HRResumeSchemaCollection) );  
```  
  
### <a name="h-creating-a-partitioned-table"></a>H. Création d'une table partitionnée  
 L'exemple suivant crée une fonction de partition pour partitionner une table ou un index en quatre partitions. L'exemple crée ensuite un schéma de partition pour spécifier les groupes de fichiers qui contiendront chacune des quatre partitions. Enfin, l'exemple crée une table qui utilise le schéma de partition. Cet exemple suppose que les groupes de fichiers existent déjà dans la base de données.  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES (1, 100, 1000) ;  
GO  
  
CREATE PARTITION SCHEME myRangePS1  
    AS PARTITION myRangePF1  
    TO (test1fg, test2fg, test3fg, test4fg) ;  
GO  
  
CREATE TABLE PartitionTable (col1 int, col2 char(10))  
    ON myRangePS1 (col1) ;  
GO  
```  
  
 En fonction des valeurs de la colonne `col1` de `PartitionTable`, les partitions sont affectées des manières suivantes.  
  
|Groupe de fichiers|test1fg|test2fg|test3fg|test4fg|  
|---------------|-------------|-------------|-------------|-------------|  
|**Partition**|1|2|3|4|  
|**Valeurs**|col 1 \<= 1|col1 > 1 AND col1 \<= 100|col1 > 100 AND col1 \<= 1 000|col1 > 1 000|  
  
### <a name="i-using-the-uniqueidentifier-data-type-in-a-column"></a>I. Utilisation du type de données uniqueidentifier dans une colonne  
 L'exemple suivant crée une table avec une colonne `uniqueidentifier`. Il utilise une contrainte PRIMARY KEY pour empêcher les utilisateurs de la table d'insérer des doublons, et la fonction `NEWSEQUENTIALID()` dans la contrainte `DEFAULT` pour fournir des valeurs aux nouvelles lignes. La propriété ROWGUIDCOL est appliquée à la colonne `uniqueidentifier` de sorte qu'elle peut être référencée en utilisant le mot clé $ROWGUID.  
  
```  
CREATE TABLE dbo.Globally_Unique_Data  
    (guid uniqueidentifier   
        CONSTRAINT Guid_Default DEFAULT   
        NEWSEQUENTIALID() ROWGUIDCOL,  
    Employee_Name varchar(60)  
    CONSTRAINT Guid_PK PRIMARY KEY (guid) );  
```  
  
### <a name="j-using-an-expression-for-a-computed-column"></a>J. Utilisation d'une expression pour une colonne calculée  
 L'exemple suivant illustre l'utilisation d'une expression (`(low + high)/2`) pour le calcul de la colonne calculée `myavg`.  
  
```  
CREATE TABLE dbo.mytable   
    ( low int, high int, myavg AS (low + high)/2 ) ;  
```  
  
### <a name="k-creating-a-computed-column-based-on-a-user-defined-type-column"></a>K. Création d'une colonne calculée basée sur une colonne de type défini par l'utilisateur  
 L'exemple suivant crée une table, avec une colonne définie comme `utf8string` dont le type de données est défini par l'utilisateur, en supposant que l'assembly du type et le type lui-même ont déjà été créés dans la base de données active. Une deuxième colonne est définie en fonction de `utf8string`et utilise la méthode `ToString()` de **type(class)** `utf8string` pour calculer une valeur pour la colonne.  
  
```  
CREATE TABLE UDTypeTable   
    ( u utf8string, ustr AS u.ToString() PERSISTED ) ;  
```  
  
### <a name="l-using-the-username-function-for-a-computed-column"></a>L. Utilisation de la fonction USER_NAME pour une colonne calculée  
 L'exemple suivant utilise la fonction `USER_NAME()` dans la colonne `myuser_name`.  
  
```  
CREATE TABLE dbo.mylogintable  
    ( date_in datetime, user_id int, myuser_name AS USER_NAME() ) ;  
```  
  
### <a name="m-creating-a-table-that-has-a-filestream-column"></a>M. Création d'une table qui comporte une colonne FILESTREAM  
 L'exemple suivant crée une table qui comporte une colonne `FILESTREAM` `Photo`. Si une table comporte une un ou plusieurs colonnes `FILESTREAM`, elle doit aussi comporter une colonne `ROWGUIDCOL`.  
  
```  
CREATE TABLE dbo.EmployeePhoto  
    (  
    EmployeeId int NOT NULL PRIMARY KEY,  
    ,Photo varbinary(max) FILESTREAM NULL  
    ,MyRowGuidColumn uniqueidentifier NOT NULL ROWGUIDCOL  
        UNIQUE DEFAULT NEWID()  
    );  
```  
  
### <a name="n-creating-a-table-that-uses-row-compression"></a>N. Création d'une table qui utilise la compression de ligne  
 L'exemple suivant crée une table qui utilise la compression de ligne.  
  
```  
CREATE TABLE dbo.T1   
(c1 int, c2 nvarchar(200) )  
WITH (DATA_COMPRESSION = ROW);  
```  
  
 Pour des exemples de la compression des données supplémentaires, consultez [la Compression des données](../../relational-databases/data-compression/data-compression.md).  
  
### <a name="o-creating-a-table-that-has-sparse-columns-and-a-column-set"></a>O. Création d'une table qui comporte des colonnes éparses et un jeu de colonnes  
 Les exemples suivants montrent comment créer une table qui comporte une colonne éparse et une table qui comporte deux colonnes éparses et un jeu de colonnes. Ces exemples utilisent la syntaxe de base. Pour obtenir des exemples plus complexes, consultez [utiliser des colonnes éparses](../../relational-databases/tables/use-sparse-columns.md) et [jeux de colonnes utilisez](../../relational-databases/tables/use-column-sets.md).  
  
 Cet exemple crée une table qui comporte une colonne éparse.  
  
```  
CREATE TABLE dbo.T1  
    (c1 int PRIMARY KEY,  
    c2 varchar(50) SPARSE NULL ) ;  
```  
  
 Cet exemple crée une table qui comporte deux colonnes éparses et un jeu de colonnes nommé `CSet`.  
  
```  
CREATE TABLE T1  
    (c1 int PRIMARY KEY,  
    c2 varchar(50) SPARSE NULL,  
    c3 int SPARSE NULL,  
    CSet XML COLUMN_SET FOR ALL_SPARSE_COLUMNS ) ;  
```  
  
### <a name="p-creating-a-system-versioned-disk-based-temporal-table"></a>P. Création d’une table temporelle avec version système sur disque  
   
  
**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Les exemples suivants montrent comment créer une table temporelle liée à une table d’historique et comment créer une table temporelle liée à une table d’historique existante. Notez que la table temporelle doit avoir une clé primaire définie pour être activée pour la table doit être activé pour le contrôle de version système. Pour obtenir des exemples montrant comment ajouter ou supprimer le contrôle de version système sur une table existante, consultez le système de contrôle de version dans [exemples](../../t-sql/statements/alter-table-transact-sql.md#Example_Top). Pour les cas d’utilisation, consultez [Tables temporelles](../../relational-databases/tables/temporal-tables.md).  
  
 Cet exemple crée une nouvelle table temporelle liée à une table d’historique.  
  
```  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH (SYSTEM_VERSIONING = ON);  
```  
  
 Cet exemple crée une nouvelle table temporelle liée à une table d’historique existante.  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (SYSTEM_VERSIONING = ON   
        (HISTORY_TABLE = dbo.Department_History, DATA_CONSISTENCY_CHECK = ON )  
    );  
```  
  
### <a name="q-creating-a-system-versioned-memory-optimized-temporal-table"></a>Q. Création d’une table temporelle à système par version optimisée en mémoire  
   
  
**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 L’exemple suivant montre comment créer une système à mémoire optimisée table temporelle avec version liée à une nouvelle table d’historique sur disque.  
  
 Cet exemple crée une nouvelle table temporelle liée à une table d’historique.  
  
```  
CREATE SCHEMA History  
GO  
CREATE TABLE dbo.Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH   
    (  
        MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA,  
            SYSTEM_VERSIONING = ON ( HISTORY_TABLE = History.DepartmentHistory )   
    );  
```  
  
 Cet exemple crée une nouvelle table temporelle liée à une table d’historique existante.  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (SYSTEM_VERSIONING = ON   
        (HISTORY_TABLE = dbo.Department_History, DATA_CONSISTENCY_CHECK = ON )  
    );  
```  
  
### <a name="r-creating-a-table-with-encrypted-columns"></a>R. Création d’une table avec des colonnes chiffrées  
 L’exemple suivant crée une table avec deux colonnes chiffrées. Pour plus d’informations, consultez [Always Encrypted &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
  
```  
CREATE TABLE Customers (  
    CustName nvarchar(60)   
        ENCRYPTED WITH   
            (  
             COLUMN_ENCRYPTION_KEY = MyCEK,  
             ENCRYPTION_TYPE = RANDOMIZED,  
             ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
            ),   
    SSN varchar(11) COLLATE  Latin1_General_BIN2  
        ENCRYPTED WITH   
            (  
             COLUMN_ENCRYPTION_KEY = MyCEK,  
             ENCRYPTION_TYPE = DETERMINISTIC ,  
             ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
            ),   
    Age int NULL  
);  
```

### <a name="s-create-an-inline-filtered-index"></a>S. Créer un index filtré inline 
Crée des tables avec un index filtré inline.
  
  ```
  CREATE TABLE t1 
 (
      c1 int,
      index IX1  (c1) WHERE c1 > 0   
 )
GO
 ```
 
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [COLUMNPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DROP INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/drop-index-transact-sql.md)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helpconstraint &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpconstraint-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_spaceused &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)  
  
  


