---
title: "Méthode getSchemas () | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.getSchemas
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: adba0ee6-ff6d-4215-b646-62c735be3fe9
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 675d5ab7e20a5d7364721319aba56a7919a255d9
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getschemas-method-"></a>Méthode getSchemas ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les noms de schémas disponibles dans la base de données actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getSchemas()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSchemas est spécifiée par la méthode getSchemas dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getSchemas contient les informations suivantes :  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**Chaîne**|Le nom du schéma.|  
|TABLE_CATALOG|**Chaîne**|Nom de catalogue pour le schéma.|  
  
 Les résultats sont classés par TABLE_CATALOG, puis par TABLE_SCHEM. Chaque ligne inclut TABLE_SCHEM comme première colonne et TABLE_CATALOG comme deuxième.  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getSchemas, consultez « sys.schemas (Transact-SQL) » dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] la documentation en ligne.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getSchemas pour retourner des informations sur le catalogue et ses noms de schéma associé dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] lorsque l’argument de connexion spécifie la base de données à utiliser.  
  
```  
public static void executeGetSchemas(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getSchemas();  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
