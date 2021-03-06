---
title: Vérification de la prise en charge de la fonctionnalité et la variabilité | Documents Microsoft
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
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43e2a044237f1aeb9c63bcac4bc0aa9733f4c9ea
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="checking-feature-support-and-variability"></a>Vérification de la prise en charge de la fonctionnalité et la variabilité
Pour vérifier la prise en charge de la fonctionnalité et la variabilité, les applications appellent généralement **SQLGetInfo**, **SQLGetFunctions**, et **SQLGetTypeInfo**. Un bon point de départ est niveaux de conformité grammaire SQL et les API du pilote. Elles décrivent les grands niveaux de prise en charge de la fonctionnalité. L’application peut ensuite appeler **SQLGetInfo** avec d’autres options pour déterminer la prise en charge ou la variabilité des fonctionnalités, il a besoin, **SQLGetFunctions** pour déterminer si elle doit au-delà du niveau de conformité retourné sont prises en charge, et **SQLGetTypeInfo** pour déterminer quels types de données SQL sont prises en charge.  
  
 Une application peut déterminer si un attribut d’instruction ou de la connexion est prise en charge en appelant **SQLSetStmtAttr** ou **SQLSetConnectAttr** avec cet attribut. Si la fonction retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, l’attribut est pris en charge ; Si elle retourne SQL_ERROR et SQLSTATE HYC00 (fonctionnalité facultative non implémentée), l’attribut n’est pas pris en charge.  
  
 Les applications peuvent également déterminer une quantité limitée d’informations avant de vous connecter au pilote en appelant **SQLDrivers**.
