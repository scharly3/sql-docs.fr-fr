---
title: Commande UNIQUE SET | Documents Microsoft
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
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f0e73315f1dca11f4b43d743e0b9dd3feb31bbab
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="set-unique-command"></a>Commande UNIQUE SET
Spécifie si les enregistrements avec les valeurs de clés d’index en double sont conservées dans un fichier d’index.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 Spécifie que tout enregistrement avec une valeur de clé d’index en double ne pas être inclus dans le fichier d’index. Seul le premier enregistrement avec la valeur de clé d’index d’origine est inclus dans le fichier d’index.  
  
 OFF  
 (Par défaut). Spécifie que les enregistrements avec les valeurs de clés d’index en double inclus dans le fichier d’index.  
  
## <a name="remarks"></a>Notes  
 Un fichier d’index conserve son paramètre de valeur UNIQUE lorsque vous émettez la RÉINDEXATION. Pour plus d’informations, consultez [INDEX](../../odbc/microsoft/index-command.md).
