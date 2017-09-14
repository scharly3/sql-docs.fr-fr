---
title: "MODIFIER la clé de chiffrement de base de données (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_ENCRYPTION_KEY_TSQL
- ALTER DATABASE ENCRYPTION
- ALTER_DATABASE_ENCRYPTION_TSQL
- ALTER DATABASE ENCRYPTION KEY
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key, alter
- ALTER DATABASE ENCRYPTION KEY
ms.assetid: f88dac4b-efe0-47ed-9808-972a4381377e
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 006862850eebb2db1d3f256ca5556016cdb02ab2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-encryption-key-transact-sql"></a>ALTER DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Modifie une clé et un certificat de chiffrement permettant de chiffrer une base de données de façon transparente. Pour plus d’informations sur le chiffrement transparent de la base de données, consultez [Transparent Data Encryption &#40; Chiffrement transparent des données &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server  
  
ALTER DATABASE ENCRYPTION KEY  
      REGENERATE WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   |  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER DATABASE ENCRYPTION KEY  
    {  
      {  
        REGENERATE WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
        [ ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name ]  
      }  
      |  
      ENCRYPTION BY SERVER   CERTIFICATE Encryptor_Name    
    }  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 REGENERATE WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
 Spécifie l'algorithme de chiffrement utilisé pour la clé de chiffrement.  
  
 CHIFFREMENT par certificat de serveur *Encryptor_Name*  
 Spécifie le nom du certificat utilisé pour chiffrer la clé de chiffrement de base de données.  
  
 CHIFFREMENT par Encryptor_Name clé asymétrique de serveur  
 Spécifie le nom de la clé asymétrique utilisée pour chiffrer la clé de chiffrement de base de données.  
  
## <a name="remarks"></a>Notes  
 Le certificat ou la clé asymétrique utilisé pour chiffrer la clé de chiffrement de base de données doit se trouver dans la base de données système principale.  
  
 La clé de chiffrement de base de données n'a pas besoin d'être régénérée lorsqu'un propriétaire de base de données (dbo) est modifié.  
  
 Lorsque la clé de chiffrement d'une base de données a été modifiée deux fois, une sauvegarde de fichier journal doit être effectuée pour rendre possible une nouvelle modification de la clé de chiffrement.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CONTROL sur la base de données et l'autorisation VIEW DEFINITION sur le certificat ou la clé asymétrique permettant de chiffrer la clé de chiffrement de base de données.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant modifie la clé de chiffrement de base de données pour qu'elle utilise l'algorithme `AES_256`.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER DATABASE ENCRYPTION KEY  
REGENERATE WITH ALGORITHM = AES_256;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'exemple suivant modifie la clé de chiffrement de base de données pour qu'elle utilise l'algorithme `AES_256`.  
  
```  
-- Uses AdventureWorks  
  
ALTER DATABASE ENCRYPTION KEY  
REGENERATE WITH ALGORITHM = AES_256;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Chiffrement transparent des données &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Chiffrement SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [SQL Server et clés de chiffrement de base de données &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CRÉER une clé de chiffrement de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [SUPPRIMER la clé de chiffrement de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
 [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
  
  

