---
title: Fonction de SQLGetPoolID | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e665ceedb5faec816a6e17a763dad0b3d1ba360
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetpoolid-function"></a>SQLGetPoolID (fonction)
**Mise en conformité**  
 Version introduite : La mise en conformité des normes 3,81 ODBC : ODBC  
  
 **Résumé**  
 **SQLGetPoolID** récupère l’ID de pool.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Arguments  
 *hDbcInfoToken*  
 [Entrée] Descripteur du jeton qui contient toutes les informations de connexion.  
  
 *pPoolID*  
 [Sortie] L’ID du pool, qui est utilisé pour identifier un ensemble de connexions qui peuvent être utilisées indifféremment (éventuellement nécessitant une réinitialisation supplémentaire).  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetPoolID** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, le Gestionnaire de pilotes utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et un **gérer** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Notes  
 **SQLGetPoolID** est utilisée pour obtenir l’ID du pool reçoit un jeu d’informations de connexion (à partir de **SQLSetConnectAttrForDbcInfo**, **SQLSetDriverConnectInfo**, et  **SQLSetConnectInfo**). Ce pool d’ID est utilisé pour identifier un ensemble de connexions qui peuvent être utilisées indifféremment (éventuellement nécessitant une réinitialisation supplémentaire). L’ID du pool sera utilisé pour identifier le pool de connexions pour ce groupe de connexions.  
  
 Chaque fois qu’un pilote retourne SQL_ERROR ou SQL_INVALID_HANDLE, le Gestionnaire de pilotes retourne l’erreur à l’application (dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) ou [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Chaque fois qu’un pilote retourne SQL_SUCCESS_WITH_INFO, le Gestionnaire de pilotes obtiendra les informations de diagnostic à partir de *hDbcInfoToken*et retourne SQL_SUCCESS_WITH_INFO, à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Les applications ne doivent pas appeler cette fonction directement. Un pilote ODBC qui prend en charge le regroupement de connexions prenant en charge les pilotes doit implémenter cette fonction.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Le regroupement de connexions prenant en charge les pilotes](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
