---
title: 'SQL à c : GUID | Documents Microsoft'
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
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a0e4d11048f532f91cc4fc06f85f6c1e355d1d4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sql-to-c-guid"></a>SQL à c : GUID
L’identificateur pour le type de données GUID ODBC SQL est :  
  
 SQL_GUID  
  
 Le tableau suivant présente les types de données à laquelle les données de GUID SQL peuvent être converties à ODBC C. Pour obtenir une explication des colonnes et des termes du contrat de la table, consultez [conversion des données à partir de SQL pour Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificateur de type C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > longueur en octets de caractères|data|36|n/a|  
||*BufferLength* < 37|Indéfini|Indéfini|22003|  
|SQL_C_WCHAR|*BufferLength* > longueur des caractères|data|36|n/a|  
||*BufferLength* < 37|Indéfini|Indéfini|22003|  
|SQL_C_BINARY|Longueur en octets de données \< =  *BufferLength*|data|Longueur des données en octets|n/a|  
||Longueur en octets de données > *BufferLength*|Indéfini|Indéfini|22003|  
|SQL_C_GUID|Aucun [a]|data|16 [b]|n/a|  
  
 [a] la valeur de *BufferLength* est ignorée pour cette conversion. Le pilote part du principe que la taille de **TargetValuePtr* est la taille du type de données C.  
  
 [b] Il s’agit de la taille du type de données C correspondante.
