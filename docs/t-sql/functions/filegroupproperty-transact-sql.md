---
title: FILEGROUPPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILEGROUPPROPERTY_TSQL
- FILEGROUPPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], property values
- FILEGROUPPROPERTY function
- viewing filegroup properties
- displaying filegroup properties
ms.assetid: b3a930e6-df05-4034-929c-f681f5f6fc6e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06a63d753f2f38864889dc78b24e7ff47e78c331
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la valeur de propriété du groupe de fichiers indiquée d'après leur nom.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FILEGROUPPROPERTY ( filegroup_name , property )  
```  
  
## <a name="arguments"></a>Arguments  
 *filegroup_name*  
 Expression de type **sysname** représentant le nom du groupe de fichiers dont les informations relatives à la propriété nommée doivent être renvoyées.  
  
 *property*  
 Expression de type **varchar(128)** qui contient le nom de la propriété du groupe de fichiers à retourner. *property* peut avoir l’une des valeurs suivantes.  
  
|Valeur|Description|Valeur renvoyée|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Groupe de fichiers en lecture seule.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Entrée non valide.|  
|**IsUserDefinedFG**|Groupe de fichiers défini par l'utilisateur.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Entrée non valide.|  
|**IsDefault**|Groupe de fichiers par défaut.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Entrée non valide.|  
  
## <a name="return-types"></a>Types de retour  
 **Int**  
  
## <a name="remarks"></a>Notes   
 *filegroup_name* correspond à la colonne **name** de la vue de catalogue **sys.filegroups**.  
  
## <a name="examples"></a>Exemples  
 Cet exemple retourne le paramètre de la propriété `IsDefault` relatif au groupe de fichiers principal de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
  
SELECT FILEGROUPPROPERTY('PRIMARY', 'IsDefault') AS 'Default Filegroup';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Default Filegroup   
---------------------   
1  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a> Voir aussi  
 [FILEGROUP_ID &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
