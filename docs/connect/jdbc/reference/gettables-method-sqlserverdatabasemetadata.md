---
title: "Méthode getTables (SQLServerDatabaseMetaData) | Documents Microsoft"
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
apiname: SQLServerDatabaseMetaData.getTables
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: a7514673-3457-4541-9560-28a8284ad9e3
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c469b56d30e93ba96378df87490be5cea83d8c2a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="gettables-method-sqlserverdatabasemetadata"></a>Méthode getTables (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des tables disponibles dans le modèle de nom de catalogue, de schéma ou de table donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getTables(java.lang.String catalog,  
                                    java.lang.String schema,  
                                    java.lang.String table,  
                                    java.lang.String[] types)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalogue*  
  
 A **chaîne** qui contient le nom du catalogue. La spécification d'une valeur Null pour ce paramètre indique que le nom du catalogue n'a pas besoin d'être utilisé.  
  
 *schéma*  
  
 A **chaîne** qui contient le modèle de nom de schéma. La spécification d'une valeur Null pour ce paramètre indique que le nom du schéma n'a pas besoin d'être utilisé.  
  
 *tableName*  
  
 A **chaîne** qui contient le modèle de nom de table.  
  
 *types de*  
  
 Tableau de chaînes qui contient les types de tables à inclure. Null indique que tous les types de tables doivent être inclus.  
  
## <a name="return-value"></a>Valeur retournée  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTables est spécifiée par la méthode getTables dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getTables contient les informations suivantes :  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**Chaîne**|Le nom de la base de données dans laquelle réside la table spécifiée.|  
|TABLE_SCHEM|**Chaîne**|Nom du schéma de table.|  
|TABLE_NAME|**Chaîne**|Le nom de la table.|  
|TABLE_TYPE|**Chaîne**|Le type de table.|  
|REMARKS|**Chaîne**|Description de la table.<br /><br /> **Remarque :** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] ne retourne pas une valeur pour cette colonne.|  
|TYPE_CAT|**Chaîne**|Non pris en charge par le pilote JDBC.|  
|TYPE_SCHEM|**Chaîne**|Non pris en charge par le pilote JDBC.|  
|TYPE_NAME|**Chaîne**|Non pris en charge par le pilote JDBC.|  
|SELF_REFERENCING_COL_NAME|**Chaîne**|Non pris en charge par le pilote JDBC.|  
|REF_GENERATION|**Chaîne**|Non pris en charge par le pilote JDBC.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getTables, consultez « sp_tables (Transact-SQL) » dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] la documentation en ligne.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getTables pour retourner les informations de description de table pour la table Person.Contact dans le [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] base de données exemple.  
  
```  
public static void executeGetTables(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTables("AdventureWorks", "Person", "Contact", null);  
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
  
  
