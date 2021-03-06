---
title: Définition des champs de descripteur | Documents Microsoft
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
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ceadd4fd1474c934ff147290761d9cb99a4089b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="setting-descriptor-fields"></a>Définition des champs de descripteur
Pour modifier les champs d’un descripteur, une application peut appeler **SQLSetDescField**. Certains champs sont en lecture seule et ne peut pas être définies. (Consultez la [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) description de fonction.)  
  
 Champs d’enregistrement descripteur sont définies avec un numéro d’enregistrement (*RecNumber*) de temps 1 ou version ultérieure, les champs d’en-tête de descripteur sont définies avec un numéro d’enregistrement de 0. Un numéro d’enregistrement de 0 est également utilisé pour définir les champs de signet, conformément à la convention que les signets sont contenus dans la colonne 0. Cela risque de laisser l’impression que les champs de signet sont contenus dans l’en-tête de descripteur, mais cela n’est pas le cas. Champs de signet sont distincts des champs d’en-tête.  
  
 Lors de la définition des champs individuellement, l’application doit suivre l’ordre défini dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Définition de certains champs entraîne le pilote définir d’autres champs. Cela garantit que le descripteur est toujours prêt à utiliser une fois que l’application a spécifié un type de données. Lorsque l’application définit le champ SQL_DESC_TYPE, le pilote vérifie que les autres champs qui spécifient le type sont valides et cohérents.  
  
 Si un appel de fonction qui est définie à un champ de descripteur échoue, le contenu du champ de descripteur n’est pas défini après l’appel de fonction qui a échoué.
