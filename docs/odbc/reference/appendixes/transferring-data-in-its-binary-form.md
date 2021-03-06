---
title: Transfert de données dans sa forme binaire | Documents Microsoft
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
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 489ce7115a312a8f2d171d839393b9ead695ef48
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="transferring-data-in-its-binary-form"></a>Transfert de données dans sa forme binaire
Une application peut transférer en toute sécurité des données (sous la forme interne utilisée par un SGBD spécifié) entre les deux sources de données qui utilisent le même SGBD et la plateforme matérielle. Pour un élément de données, les types de données SQL doivent être la même dans les sources de données source et cible. Le type de données C est SQL_C_BINARY.  
  
 Lorsque l’application appelle **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData** pour extraire les données de la source de données, le pilote récupère les données à partir de la source de données et les transfère, sans conversion, à un emplacement de stockage de type SQL_C_BINARY. Lorsque l’application appelle **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData ou SQLSetPos** pour envoyer les données à la source de données cible, le pilote récupère les données à partir de l’emplacement de stockage et les transfère, sans conversion, à la source de données cible.  
  
> [!NOTE]  
>  Les applications qui transfèrent des données (à l’exception des données binaires) de cette manière ne sont pas interopérables entre SGBD.  
  
 **SQLCopyDesc** peut être utilisé pour copier les liaisons de lignes de la source SGBD aux liaisons de paramètre dans le SGBD cible.
